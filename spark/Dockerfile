FROM continuumio/miniconda3:latest

# Create environment and install geospatial + Spark packages
RUN conda create -n evlake python=3.10 \
    pyspark=3.5 geopandas rasterio fiona pyproj shapely -c conda-forge -y

# Activate environment and install additional Python packages
RUN /bin/bash -c "source activate evlake && pip install delta-spark==3.2 apache-sedona==1.5.1 jupyter"

# Set working directory
WORKDIR /opt/workspace

# Copy and set permissions for startup script
COPY start.sh /opt/workspace/start.sh
RUN chmod +x /opt/workspace/start.sh

# Default command: launch startup script
CMD ["/opt/workspace/start.sh"]

