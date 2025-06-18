# Use rocker/r-ver:latest as the base image
FROM rocker/r-ver:latest

# Install Python, pip, virtualenv, and curl
RUN apt-get update && apt-get install -y python3 python3-pip python3-venv wget curl

# Install uv package manager
RUN curl -LsSf https://astral.sh/uv/install.sh | sh

# Create a virtual environment and activate it
RUN python3 -m venv /opt/venv
ENV PATH="/opt/venv/bin:/root/.cargo/bin:$PATH"

# Install the tidyverse package in the R environment
RUN R -e "install.packages('tidyverse')"

# Install common libraries for the Jupyter ecosystem in the Python environment
RUN pip install jupyterlab notebook pandas numpy matplotlib seaborn

# Install Git
RUN apt-get update && apt-get install -y git

# Install Quarto
RUN wget https://github.com/quarto-dev/quarto-cli/releases/download/v1.6.40/quarto-1.6.40-linux-amd64.deb \
    && dpkg -i quarto-1.6.40-linux-amd64.deb \
    && rm quarto-1.6.40-linux-amd64.deb
