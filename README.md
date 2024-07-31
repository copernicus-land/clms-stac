# Project Structure

This project contains 4 parts including `/stacs`, `/schema`, `/scripts`, and `/tests`.

In the `/stacs` directory there are stac item and stac collection samples of a list of [Copernicus Land Monitoring Service products](https://git.sinergise.com/sh-vas/sh-vas/-/issues/1603) (CLMS products) and a stac catalog sample.

The `/schema` directory contains [JSON scehma](https://json-schema.org/) for validating STAC items and collections of CLMS products. Each CLMS product is paired with a shema which defines the schema of the item and the collection.

The `/tests` directory contains tests to validate STAC items, collections, and catalogs against the core STAC specification, the extensions, and the corresponding product schemas.

The `/scripts` directory contains the CLMS STAC tools which can be used to create STAC items and collections via reading the data itself or the metadata file.

In the root directory, there are wrapper scripts which can walk through the CLMS products stored in the EEA CWS and use the CLMS STAC tools in the `/scripts` directory to generate STAC items and collection for the full archive.

<pre>
clms-stac/
│
├── .gitignore                    # Gitignore file to specify ignored files and directories
├── .github/workflows             # GitHub CI actions
├── .pre-commit-config.yaml        # Basic pre-commit config file
├── pyproject.toml                # TOML configuration file often used for tool settings and project metadata
├── README.md                     # Project README with an overview, setup, and usage instructions
├── requirements.txt              # File listing project dependencies
├── requirements-dev.txt          # File listing project dependencies for development
├── scripts/                      # Directory for CLMS STAC tools
├── schema/                       # Directory for product schemas
├── tests/                        # Directory for tests
├── create_clc_collection.py      # Wrapper to create CLC collection from data archive in CWS
├── create_clcplus_collection.py  # Wrapper to create CLC plus collection from data archive in CWS
├── create_euhydro_collection.py  # Wrapper to create EU-Hydro collection from data archive in CWS
├── create_ibu10m_collection.py   # Wrapper to create Imperviousness Built-up collection from data archive in CWS
├── create_ibu10m_items.py        # Wrapper to create Imperviousness Built-up items from data archive in CWS
├── create_n2k_collection.py      # Wrapper to create Natura2000 collection from data archive in CWS
├── create_uabh_collection.py     # Wrapper to create Urban Atlas Building Height collection from data archive in CWS
├── create_uabh_items.py          # Wrapper to create Urban Atlas Building Height items from data archive in CWS
├── create_vpp_collection.py      # Wrapper to create Vegetation Phenology and Productivity collectioin from S3 bucket
└── create_vpp_items.py           # Wrapper to create Vegetation Phenology and Productivity items from S3 bucket

</pre>

# Contribution

To add support to other CLMS porducts, please follow the worflow described below.

1. Manually create a sample STAC item/collection of a CLMS product and use it as a starting point of the duscussion with the data provider.

2. After the STAC item/collection of a CLMS product is defined, create a JSON schema for validation purpose in production.

3. Prepare scripts which read the data itself or the metadata file and compile a STAC item/collection.

4. If needed, implement scripts in EEA CWS and generate STAC itmes/collections for the CLMS archive.

# Branches

- `main`: The main branch which contains the latest stable version.

- `develop`: The develop branch for contributers with no EEA CWS access.

- `feat/stac-prod-crunch`: The branch which contains thr working version in EEA CWS environment.
