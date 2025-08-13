# Caddy Proxy Demo: Jupyter & Dash

This demo illustrates using [Caddy](https://caddyserver.com/) as a reverse proxy for both Jupyter Notebook and Dash applications. It highlights a common issue when embedding Dash apps in Jupyter: Dash still serves its iframe content on port `8050` instead of the proxied port (e.g., `1234`), even when `DASH_PROXY` is set.

## Features

- **Caddy** proxies requests to Jupyter and Dash.
- **Jupyter Notebook** runs on a backend port.
- **Dash app** is embedded in Jupyter via an iframe.
- Demonstrates Dash's iframe content not respecting the proxy port.

## Problem Illustrated

When embedding a Dash app in Jupyter and proxying with Caddy:

- The Dash iframe in Jupyter points to `localhost:8050` (Dash's default port).
- Even with `DASH_PROXY` set, Dash does not serve iframe content on the proxied port (`1234`).
- This can cause issues with access, authentication, and cross-origin requests.

## Usage

`pixi run start` will start both Caddy and Jupyter. Open http://localhost:1234/jupyter/lab/tree/dash.ipynb after the servers have started to view the Dash notebook.

## Known Issue

Running the cell will print the message `Dash app running on http://127.0.0.1:8050/dash/` which is the wrong url. It should be [http://127.0.0.1:1234/dash/]().

## References

- [Caddy Documentation](https://caddyserver.com/docs/)
- [Dash in Jupyter](https://dash.plotly.com/in-jupyter)
- [Dash Proxying](https://dash.plotly.com/deployment)
