FROM continuumio/miniconda3:latest
RUN conda install -c conda-forge pandas geopandas shapely requests -y
RUN pip install routee nrel-pyapi
WORKDIR /workspace
COPY routee_pipeline.py /workspace/