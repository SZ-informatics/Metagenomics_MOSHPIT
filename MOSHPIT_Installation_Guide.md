# MOSHPIT Installation Guide for Mac (Apple Silicon)

## Goal

Install QIIME2 MOSHPIT on a MacBook (Apple Silicon) using Docker.

------------------------------------------------------------------------

## Step 1: Install Anaconda or Miniconda

Verify conda:

``` bash
conda --version
```

Expected:

``` bash
conda 24.x.x
```

------------------------------------------------------------------------

## Step 2: Install Mamba (optional)

``` bash
conda install -n base -c conda-forge mamba
```

Verify:

``` bash
mamba --version
```

------------------------------------------------------------------------

## Step 3: Verify QIIME Amplicon environment

List environments:

``` bash
conda env list
```

Activate:

``` bash
conda activate qiime2-amplicon-2024.10
```

Check:

``` bash
qiime info
```

------------------------------------------------------------------------

## Step 4: Install Docker Desktop

Download:

https://www.docker.com/products/docker-desktop/

Install and open Docker Desktop.

Wait until Docker says:

"Docker Desktop is running"

Verify:

``` bash
docker --version
```

Expected:

``` bash
Docker version 29.x.x
```

------------------------------------------------------------------------

## Step 5: Open project directory

Example:

``` bash
cd ~/Bio-informatics
```

------------------------------------------------------------------------

## Step 6: Start MOSHPIT

``` bash
docker run -v $(pwd):/data -it quay.io/qiime2/moshpit:2026.4 /bin/bash
```

Expected:

``` bash
(rachis-moshpit-2026.4) root@xxxxx:/data#
```

------------------------------------------------------------------------

## Step 7: Verify installation

Inside container:

``` bash
qiime info
```

Expected output includes:

-   QIIME release: 2026.4
-   Plugins loaded
-   Python version

------------------------------------------------------------------------

## Step 8: Exit container

``` bash
exit
```

------------------------------------------------------------------------

## Optional: Create startup shortcut

Run once:

``` bash
echo 'alias moshpit="docker run -v \$(pwd):/data -it quay.io/qiime2/moshpit:2026.4 /bin/bash"' >> ~/.zshrc
```

Load:

``` bash
source ~/.zshrc
```

Future startup:

``` bash
cd ~/Bio-informatics
moshpit
```

------------------------------------------------------------------------

## Notes

-   MOSHPIT Linux conda YAML does not install directly on macOS.
-   Docker provides a Linux environment on Mac.
-   Apple Silicon Macs may display amd64/arm64 warnings; these are
    expected.
-   Files in `/data` are synchronized with your local Mac folder.
