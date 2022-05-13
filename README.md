# Prez

Prez is a Linked Data API framework tool that delivers read-only access to Knowledge Graph data according to particular domain _profiles_.

Prez comes in two main profile flavours:

- _VocPrez_ - for vocabularies, based on the [SKOS](https://www.w3.org/TR/skos-reference/) data model
- _SpacePrez_ - for spatial data, based on [OGC API](https://docs.ogc.org/is/17-069r3/17-069r3.html) specification and the [GeoSPARQL](https://opengeospatial.github.io/ogc-geosparql/geosparql11/spec.html) data model

Prez is pretty straight-forward to install and operate and while being high-performance, using modern [FastAPI](https://fastapi.tiangolo.com/) Python web framework. 

Prez is quite simple and expects "high quality" data to work well. By requiring that you create high quality for it, Prez ensures your value is retained in your data and not in a black box application: you remain in control!

## Development Schedule

The following features and other updates are planned:

Feature | Timeline
--- | ---
Improved installation documentation | Mid/late May, 2022
CQL filtering | Late May, 2022 
Profile auto-creation | Late May, 2022

## Installation
Install using Poetry (optional), which you can install [here](https://python-poetry.org/docs/#installation) (recommended), or by running:

```bash
pip install poetry 
```

Then run `poetry install` in the root directory, `Prez/`.

Otherwise install using `pip` as normal:

```bash
pip install -r requirements.txt 
```

## Deploying
To get started without any configuration, simply run `python3 app.py` in the `Prez/prez/` directory.

Two additional repos are required to properly update data & customise a Prez instance for deployment:

### 1. Updating Prez Data
Each *Prez expects data to conform to a particular format. For each *Prez used in your instance, fork/clone each of these repos for updating data:

- VocPrez - [surround-prez-vocabs](https://github.com/surroundaustralia/surround-prez-vocabs)
- SpacePrez - [surround-prez-features](https://github.com/surroundaustralia/surround-prez-features)

Each repo contains a validate & update script. Refer to each repo's documentation on how to use them.

### 2. Customisation & Deployment
Prez is designed to run in a containerised environment. Configuring & theming Prez is done by following [surround-prez-theme](https://github.com/surroundaustralia/surround-prez-theme). Fork/clone this repo to run/deploy your own Prez instance. Refer to the repo's documentation on how to configure.

## Application Structure
The standard process for an entity endpoint is as follows:

1. An endpoint within a router is accessed (in `routers/`)
2. Endpoint calls SPARQL service to POST a SPARQL query (in `services/`)
3. The resulting RDFlib Graph is ingested by a model object (in `models/`)
4. A renderer object is created which uses the model object (in `renderers/`)
5. The endpoint returns the renderer's `render()` function
    - The response can be a renderered template (in `templates/`)

## Dev Dependencies

- SASS
    - Run the SASS watcher from the `sass/` folder like so:
        - If using dart-sass: `sass --no-source-map --watch main.scss ../css/index.css`
        - If using node-sass: `sass --source-map=none --watch main.scss ../css/index.css`

## License

This version of Prez and the contents of this repository are also available under the [BSD-3-Clause License](https://opensource.org/licenses/BSD-3-Clause). See [this repository's LICENSE](https://github.com/surroundaustralia/Prez/blob/main/LICENSE) file for details.


## Contributing

We love contributions to this tool and encourage you to create Issues in this repositories Issue Tracker as well as submitting Pull Requests with your own updates.

## Contact

This tool is actively deveoped and supported by [SURROUND Australia Pty Ltd](https://surroundaustalia.com). Please contact SURROUND either by creating issues in the [Issue Tracker](https://github.com/surroundaustralia/Prez/issues) or directly emailing the lead developers:

**Jamie Feiss**  
<jamie.feiss@surroundaustralia.com>

**David Habgood**  
<david.habgood@surroundaustralia.com>
