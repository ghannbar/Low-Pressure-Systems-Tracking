<<<<<<< HEAD
# Low-Pressure Systems Tracking

A set of local web tools for downloading NCEP/NCAR Reanalysis geopotential-height (`hgt`) data and detecting and tracking low-pressure systems (cyclones) in it. Each tool is a single-file Flask app with a browser UI and live progress streaming.

| Folder | Script | What it does |
|---|---|---|
| [`Downloader/`](Downloader) | `Downloader.py` | Downloads yearly `hgt.<year>.nc` files from NOAA PSL with resumable downloads, a manifest-based cache, and per-file progress. |
| [`KamFeshar/`](KamFeshar) | `KamFeshar.py` | Scans a local folder of `.nc` files and detects low-pressure centers (600 km radius, 1.0σ), with filters for years, months, levels, and area. Results can be exported as CSV. |
| [`MAIN/`](MAIN) | `app.py` | The complete pipeline: download + detection + a 7-stage cyclone tracker (prominence-based detection, feature extraction, motion prediction, Mahalanobis gating, Hungarian assignment, track lifecycle, and merge-event analysis), with a Leaflet map. |

## Requirements

- Python 3.9 or newer
- Packages listed in [`requirements.txt`](requirements.txt)
- An internet connection for downloading data. `MAIN` also loads Leaflet from unpkg and map tiles from OpenStreetMap

`scipy` is optional but recommended. Without it, the detector falls back to a numpy implementation and the tracker to a greedy assignment instead of the Hungarian algorithm.

## Quick start

```bash
git clone https://github.com/<your-username>/FASHAR.git
cd FASHAR

python -m venv .venv
source .venv/bin/activate        # Windows: .venv\Scripts\activate
pip install -r requirements.txt

cd MAIN
python app.py
```

Then open <http://127.0.0.1:5000>.

Each app listens on port 5000, so run only one at a time. To use another tool, `cd` into its folder and run its script (`python Downloader.py` or `python KamFeshar.py`).

## Data and output folders

Apps create these folders in the directory you run them from:

- `hgt_cache/` holds the downloaded `.nc` files and `manifest.json`. Yearly files can be large, so make sure you have disk space.
- `lows_output/` (`MAIN` only) holds generated result files.

Both are in `.gitignore`. If you already have the `.nc` files, put them in `hgt_cache/` and the apps will use them without downloading.

## Data source

Data comes from the [NCEP/NCAR Reanalysis 1](https://psl.noaa.gov/data/gridded/data.ncep.reanalysis.html) daily pressure-level dataset, provided by NOAA Physical Sciences Laboratory. Please follow the dataset's terms of use and cite it as NOAA/PSL requests.

## Security note

The apps bind to `127.0.0.1` only and have no authentication. They are meant for local use. Don't expose them to a network or the internet as they are.

## License

[MIT](LICENSE)
=======
# Low-Pressure-Systems-Tracking
 Low-Pressure Systems Tracking is a Python-based meteorological analysis project focused on detecting, analyzing, and tracking low-pressure systems using weather data. It provides tools for identifying low-pressure centers, analyzing atmospheric patterns, and visualizing meteorological features to support weather analysis and research.
>>>>>>> 95064ce29b223477e25badaa01dbcef63e945159
