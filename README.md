# MtnMe.sh
MtnMesh GitHub Pages

Edit the content in `docs/`, PR's welcomed!

## Running Locally

You have to build the docker container for serving the website to include a few plugins. [See this website for more details.](https://squidfunk.github.io/mkdocs-material/getting-started/#with-docker)

```bash
docker build -t mtnmesh:latest .
```

To run, use the following command:

```bash
docker run --rm -it -p 8000:8000 -v ${PWD}:/docs mtnmesh:latest
```

[View Local Dev Site Here](http://localhost:8000/)
