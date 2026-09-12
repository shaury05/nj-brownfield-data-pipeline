# Essex County Brownfield Revitalization Data Pipeline

**Author:** Shaury Pratap Singh

## 📌 Project Overview
This project demonstrates an end-to-end data pipeline built for environmental consulting and community systems management. It takes raw government environmental data and processes it through a relational database, geospatial mapping software, and an automated email marketing campaign to simulate a complete community engagement lifecycle.

## 🗄️ Dataset
* **Source:** New Jersey Department of Environmental Protection (NJDEP) - [DEP DataMiner](https://njems.nj.gov/DataMiner#)
* **Report Name:** The Known and Suspected Sites by County
* **Data Access Path:** `Home > Search By Category > Site Remediation > [The Known and Suspected Sites by County] > Report Criteria`
* **Description:** This official state report enables the requestor to view a list of both known and suspected contaminated sites within a specified county. For this project, the dataset was queried specifically for **Essex County**.
* **Fields Extracted:** Site ID, Current Site Name, Address, Municipality, Zip Code, and Contamination Status.

## 🛠️ Technology Stack
* **Data Engineering:** Python, Pandas
* **Geocoding API:** GeoPy (ArcGIS geocoder)
* **Relational Database / CRM:** Airtable ([View Live CRM Database Here](https://airtable.com/app5cSrq71l9akSUH/shrR6GTj2gAKnB3x2))
* **Geospatial Mapping:** ArcGIS Online
* **Community Engagement:** Constant Contact

## 🚀 Workflow & Process

### Step 1: Data Extraction & CRM Architecture (Airtable)
* Extracted raw Site Reports from the NJDEP DataMiner portal.
* Designed a relational database in Airtable.
* Created a primary `Known and Suspected Site Report` table and linked it to a `Stakeholders` table via Foreign Keys, allowing seamless assignment of community leaders to specific environmental sites.

### Step 2: The Geocoding Challenge (Python)
* **The Problem:** The raw data contained dirty government formats (number ranges like `1007 1009 BROAD ST`, intersections, and tags like `Newark City`). Open-source geocoders (like OpenStreetMap/Nominatim) failed to parse 96% of the addresses, leading to dropped map pins. Bulk geocoding inside ArcGIS Pro is often hidden behind enterprise credit paywalls.
* **The Solution:** Wrote a custom Python script using `pandas` to dynamically clean the municipal strings. Switched the geocoding engine to the `ArcGIS` API via the `geopy` library, utilizing superior parsing logic to bypass paywalls and successfully extract exact Latitude/Longitude coordinates for all 50 sites.

### Step 3: Geospatial Visualization (ArcGIS Online)
* Imported the Python-enriched CSV into ArcGIS Online.
* Mapped the exact coordinates to create an interactive visual dashboard of environmental liabilities across Newark, Irvington, and Maplewood.

### Step 4: Marketing & Outreach (Constant Contact)
* Designed a targeted community engagement campaign.
* Embedded the ArcGIS visualizations into a clean, professional email template.
* Drafted copy inviting stakeholders to a simulated Town Hall meeting to discuss the environmental assessment of specific mapped sites.

## 📂 Repository Structure
* `/data` - Contains the raw NJDEP data and the final enriched CSV with coordinates.
* `/scripts` - Contains the `geocode_brownfields.py` file used to clean data and hit the ArcGIS API.
* `/assets` - Screenshots of the Airtable CRM setup, the ArcGIS map, and the final Constant Contact email template.
* `/docs` - The detailed project report PDF outlining the iterative problem-solving process.
