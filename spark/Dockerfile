FROM continuumio/miniconda3

# Create Conda environment with Python + geospatial + Spark
RUN conda create -n evlake python=3.10 \
    pyspark=3.5 geopandas rasterio fiona pyproj shapely -c conda-forge -y

# Activate env and install pip-only packages
SHELL ["conda", "run", "-n", "evlake", "/bin/bash", "-c"]
RUN pip install delta-spark==3.2 apache-sedona==1.5.1

WORKDIR /opt/workspace

