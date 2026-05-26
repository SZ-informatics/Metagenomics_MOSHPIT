# MOSHPIT Workflow on Mac (Apple Silicon + Docker)

## Daily Startup Workflow

### Step 1: Open VS Code

Open your project folder:

`~/Bio-informatics`

------------------------------------------------------------------------

### Step 2: Open a terminal

In VS Code:

**Terminal → New Terminal**

------------------------------------------------------------------------

### Step 3: Navigate to project folder

``` bash
cd ~/Bio-informatics
```

------------------------------------------------------------------------

### Step 4: Start MOSHPIT Docker container

``` bash
docker run   -v $(pwd):/data   -it quay.io/qiime2/moshpit:2026.4   /bin/bash
```

Expected prompt:

``` bash
(rachis-moshpit-2026.4) root@xxxxx:/data#
```

------------------------------------------------------------------------

### Step 5: Move to working directory

Examples:

``` bash
cd 01_Qiime2_metagenomics
```

or

``` bash
cd 06_Metagenomics
```

Check files:

``` bash
ls
```

------------------------------------------------------------------------

### Step 6: Run QIIME / MOSHPIT commands

Examples:

``` bash
qiime info
```

``` bash
qiime demux summarize ...
```

``` bash
qiime feature-table summarize ...
```

------------------------------------------------------------------------

### Step 7: Exit when finished

``` bash
exit
```

------------------------------------------------------------------------

# Optional shortcut (run once only)

Create an alias:

``` bash
echo 'alias moshpit="docker run -v \$(pwd):/data -it quay.io/qiime2/moshpit:2026.4 /bin/bash"' >> ~/.zshrc
```

Activate it:

``` bash
source ~/.zshrc
```

Then future startup becomes:

``` bash
cd ~/Bio-informatics
moshpit
```

------------------------------------------------------------------------

# Notes

-   Docker must be running before using MOSHPIT.
-   Files inside `/data` are automatically synced with your Mac folder.
-   Files created in Docker appear in `~/Bio-informatics`.
-   Apple Silicon Macs may show platform warnings; Docker handles them
    automatically.
