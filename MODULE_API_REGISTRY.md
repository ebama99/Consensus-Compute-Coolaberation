# TVS Module API Registry — Comprehensive Free Tier List
**Last Updated:** 2026-03-12
**Status:** Live = active | Placeholder = implement tomorrow | Upgrade = swap existing

---

## 🔑 EXISTING KEYS ALREADY IN api_keys.json

| Key | Maps To | Module(s) | Action |
|---|---|---|---|
| `ibmq_token` + `ibmq_channel` + `ibmq_backend` | S8 IBM Quantum | Space Travel | **S8 NOW LIVE — token ready** |
| `tomorrow_io` | C1 upgrade | Climate | Upgrade Open-Meteo → Tomorrow.io |
| `newsapi` | All modules | All 4 | Tweet enrichment — daily posts |
| `serpapi` | All modules | All 4 | Web search supplement |
| `google_places` | F3 upgrade | True Crime | Enhance spatial analysis |
| `finnhub` | C-ESG | Climate | ESG + carbon company data |
| `fred` | C-Economic | Climate | Energy + economic data |
| `alpha_vantage` | C-Commodity | Climate | Carbon credit / energy prices |
| `polygon` | C-Market | Climate | Carbon/energy market data |
| `brave` | All modules | All 4 | Search enrichment |
| `anthropic` | Analysis | All 4 | Sophia analysis layer |

---

## MODULE 1 — TRUE CRIME PROTOCOL

### Live Feeds (Free, No Key)
| ID | API | Endpoint | Data Type | Phase |
|---|---|---|---|---|
| F1 | FBI Crime Data API | api.usa.gov/crime/fbi/ | UCR statistics | Statistical |
| F2 | DOJ NCVS API | bjs.ojp.gov | Victimization survey | Behavioral |
| F3 | OSM Nominatim | nominatim.openstreetmap.org | Geocoding/spatial | Spatial |
| F4 | Data.gov Public Safety | catalog.data.gov / api.data.gov | Arrest/incident records | Temporal |
| F5 | CourtListener REST v4 | courtlistener.com/help/api/rest/ | Federal case law + PACER | Behavioral |
| F6 | Nannostomus Offender API | nannostomus.com/api/ | 645K+ offender records | Behavioral |
| F7 | DOJ News API | justice.gov/developer | Prosecution outcomes | Temporal |

### Upgrade — Use Existing Key
| ID | API | Key | Enhancement |
|---|---|---|---|
| F3+ | Google Places API | `google_places` | Richer location data for crime scene spatial analysis |

### Free Placeholders (Implement Tomorrow)
| ID | API | Auth Needed | Data Type | Priority |
|---|---|---|---|---|
| F8 | NIBRS Incident API | Free key — crime-data-explorer.fr.cloud.gov | Incident-level records | HIGH |
| F9 | OpenSanctions API | None | PEPs, sanctions, wanted persons | HIGH |
| F10 | US Census Geocoder | None | Address → census tract + demographics | HIGH |
| F12 | OJJDP Statistical Briefing | None (public) | Juvenile justice data | MED |
| F13 | CourtListener Bulk / RECAP | Free — same token as F5 | Full docket filings | MED |
| F14 | Interpol Red Notices | None (public web) | International wanted persons | LOW |

### Tweet Content Sources
- NewsAPI (`newsapi`) — crime headlines
- DOJ News F7 — prosecution outcomes
- FBI UCR F1 — crime stat of the day

---

## MODULE 2 — CLIMATE FORECASTING

### Live Feeds (Free, No Key)
| ID | API | Endpoint | Data Type | Phase |
|---|---|---|---|---|
| C1 | Open-Meteo | api.open-meteo.com/v1/forecast | Temperature/wind/humidity | Awakening |
| C2 | NOAA Climate CDO | ncei.noaa.gov/cdo-web/api/v2 | Historical climate records | Awakening |
| C3 | NASA POWER | power.larc.nasa.gov/api | Solar + meteorological data | Growth |
| C4 | OpenAQ Air Quality | api.openaq.org/v3 | PM2.5, CO2 proxies | Integration |
| C5 | World Bank CO2 | api.worldbank.org (EN.ATM.CO2E.KT) | CO2 emissions | Expansion |
| C6 | USGS Earthquake | earthquake.usgs.gov/earthquakes/feed | Geophysical indicators | Transformation |
| C7 | GBIF Biodiversity | api.gbif.org/v1/occurrence/search | Species occurrence data | Empowerment |

### Upgrades — Use Existing Keys
| ID | API | Key | Enhancement |
|---|---|---|---|
| C1+ | Tomorrow.io Weather | `tomorrow_io` | Real-time + 7-day forecasts, better than Open-Meteo |
| C5+ | FRED Economic Data | `fred` | Energy prices, GDP, climate policy economic data |
| C5+ | Alpha Vantage | `alpha_vantage` | Carbon credit prices, energy commodity data |
| C5+ | Finnhub | `finnhub` | ESG scores, climate-focused company data |
| C5+ | Polygon.io | `polygon` | Carbon/energy market data |

### Free Placeholders
| ID | API | Auth Needed | Data Type | Priority |
|---|---|---|---|---|
| C8 | Copernicus CDS (ERA5) | Free account — cds.climate.copernicus.eu | Best historical reanalysis | HIGH |
| C9 | NOAA ENSO / El Niño | None (public) | Oceanic Niño Index | HIGH |
| C11 | NSIDC Arctic Sea Ice | None (public) | Polar ice extent | HIGH |
| C12 | Global Forest Watch | Free key — globalforestwatch.org | Deforestation/reforestation | MED |
| C13 | NOAA Coral Reef Watch | None (public) | Coral bleaching alerts | MED |
| C14 | NASA EARTHDATA / Jet Stream | Free key — api.nasa.gov | Atmospheric/jet stream | MED |

### Tweet Content Sources
- Open-Meteo / Tomorrow.io — daily climate stat
- World Bank CO2 — carbon trend
- GBIF — biodiversity fact of the day
- NewsAPI — climate headlines

---

## MODULE 3 — SPACE TRAVEL / QUANTUM TUNNELS

### Live Feeds (Free, No Key)
| ID | API | Endpoint | Data Type | Phase |
|---|---|---|---|---|
| S1 | NASA Exoplanet Archive | exoplanetarchive.ipac.caltech.edu/TAP | Planetary systems | Initialization |
| S2 | NASA APOD | api.nasa.gov/planetary/apod | Astronomy picture + data | Calibration |
| S3 | JPL Horizons | ssd.jpl.nasa.gov/api/horizons.api | Orbital mechanics | Optimization |
| S4 | SpaceX Launch API | api.spacexdata.com/v5/launches/latest | Launch data | Exploration |
| S5 | ISS Position | api.open-notify.org/iss-now.json | Live ISS coordinates | Synthesis |
| S6 | NASA NEO Feed | api.nasa.gov/neo/rest/v1/feed/today | Near-earth objects | Enhancement |

### Upgrade — Use Existing Key (NOW LIVE)
| ID | API | Key | Enhancement |
|---|---|---|---|
| **S8** | **IBM Quantum Runtime** | **`ibmq_token` + `ibm_torino`** | **S8 placeholder → LIVE. Hybrid quantum-classical simulation** |

### Free Placeholders
| ID | API | Auth Needed | Data Type | Priority |
|---|---|---|---|---|
| S7 | ESA Space Debris | Free account — ESA | Space debris catalog | MED |
| S9 | LIGO Gravitational Wave | None (public) | Gravitational wave events | HIGH |
| S10 | CERN Open Data | None (public) | Particle physics / exotic matter | HIGH |
| S12 | NASA Goddard CDAWeb | None (public) | Space physics / radiation | MED |
| S13 | ESA Gaia Catalog | None (public TAP) | Stellar coordinates / galactic map | MED |
| S14 | SETI Institute | TBD | Signal detection | LOW |

### Tweet Content Sources
- NASA APOD S2 — daily space image + caption
- ISS Position S5 — live ISS coordinates
- SpaceX S4 — launch updates
- NASA NEO S6 — asteroid alert or all-clear
- NewsAPI — space research headlines

---

## MODULE 4 — LONGEVITY / MEDICAL RESEARCH

### Live Feeds (Free, No Key)
| ID | API | Endpoint | Data Type | Phase |
|---|---|---|---|---|
| L1 | NCBI PubMed | eutils.ncbi.nlm.nih.gov (pubmed) | DNA methylation literature | Initialization |
| L2 | UniProt | rest.uniprot.org | Sirtuin protein data | Calibration |
| L3 | NCBI Gene | eutils.ncbi.nlm.nih.gov (gene) | SIRT1 longevity genes | Optimization |
| L4 | ClinicalTrials.gov | clinicaltrials.gov/api/v2/studies | NAD+ longevity trials | Exploration |
| L5 | OpenFDA Drug | api.fda.gov/drug/label.json | NMN / resveratrol labels | Synthesis |
| L6 | Ensembl REST | rest.ensembl.org | Genomic coordinates | Enhancement |
| L7 | Human Protein Atlas | proteinatlas.org/api | Aging-associated proteins | Validation |

### Free Placeholders
| ID | API | Auth Needed | Data Type | Priority |
|---|---|---|---|---|
| L8 | ENCODE Project | None (public) | Epigenetic chromatin / CpG | HIGH |
| L9 | GEO NCBI Epigenomics | None (public) | Methylation clock datasets | HIGH |
| L10 | Broad Institute CRISPR | None (public) | CRISPR-Cas9 CpG guides | HIGH |
| L11 | GTEx Portal | None (public) | Gene expression / NAD+ tissues | MED |
| L13 | NIH NIA Longevity | None (public) | Longevity consortium data | MED |
| L14 | WHO Global Health Observatory | None (public) | Global lifespan statistics | MED |

### Tweet Content Sources
- PubMed L1 — longevity research headline of the day
- ClinicalTrials L4 — active trial spotlight
- OpenFDA L5 — supplement / drug data point
- NewsAPI — medical research headlines

---

## DAILY TWEET SCHEDULE — 4 MODULES × 1 POST/DAY

| Time (UTC) | Module | Source APIs | Content |
|---|---|---|---|
| 08:00 | True Crime | F7 DOJ News + F1 FBI Stats + NewsAPI | Crime analysis of the day |
| 11:00 | Climate | C1 Tomorrow.io + C5 CO2 + NewsAPI | Climate data point of the day |
| 14:00 | Space Travel | S2 APOD + S5 ISS + NewsAPI | Space research highlight |
| 17:00 | Longevity | L1 PubMed + L4 ClinicalTrials + NewsAPI | Longevity science of the day |

All posts: educational analysis only, not financial/medical/legal advice. DYOR.

---

## TOTALS

| Module | Live Free | Have Key Upgrades | Free Placeholders | Grand Total |
|---|---|---|---|---|
| True Crime | 7 | 1 | 6 | **14** |
| Climate | 7 | 5 | 6 | **18** |
| Space Travel | 6 | 1 (IBM Quantum live) | 6 | **13** |
| Longevity | 7 | 0 | 6 | **13** |
| **TOTAL** | **27** | **7** | **24** | **58** |
