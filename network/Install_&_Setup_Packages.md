# Steps to Install and Stepup Packages

## Graphframe
### Install
In order to use `graphframe` spark package for pyspark network analysis, the first step is to download the `.jar` file (via this [website](https://spark-packages.org/package/graphframes/graphframes)) for `graphframe` package locally (note: here I chose the version that matches the pyspark version in midway).

Then, move the `jar` file (downloaded ) for `graphframe` package to `/network` folder on midway:
```bash
scp graphframes-0.8.2-spark3.2-s_2.12.jar tianyuec@midway3.rcc.uchicago.edu:MACS_30123/final-project-les-deux-mousquetaires/network
```

### Setup
To use it for sinteractive:
```bash
# Initiate sinteractive
sinteractive --ntasks=10 --account=macs30123

module load python spark mkl

export PYSPARK_DRIVER_PYTHON=/software/python-anaconda-2022.05-el8-x86_64/bin/python3

pyspark --jars graphframes-0.8.2-spark3.2-s_2.12.jar

# Exit pyspark
exit()

# Exit sinteractive
exit()
```

### Documentation for graphframe
- [Graphframes overview](https://graphframes.github.io/graphframes/docs/_site/index.html)
- [pygraphframes documentation](https://graphframes.github.io/graphframes/docs/_site/api/python/graphframes.html)

## node2vec
### Install
In order to use lastest `node2vec` package, the first step is to download the `.whl` file (see [here](final-project-les-deux-mousquetaires/network/node2vec-0.4.6-py3-none-any.whl)) locally via this [website](https://pypi.org/project/node2vec/#files) (or you can just directly use `pip download`).

```bash
# Move the whl file to midway
scp node2vec-*.whl tianyuec@midway3.rcc.uchicago.edu: MACS_30123/final-project-les-deux-mousquetaires/network
# Install the package
pip install final-project-les-deux-mousquetaires/network/node2vec-*.whl
```

Then, export the LD_LIBRARY_PATH to include the directory that stores `libmkl_rt.so.1` file: 
```bash
# Check directories that stores `libmkl_rt.so.1` file
find / -name "libmkl_rt.so.1" 2>/dev/null

echo 'export LD_LIBRARY_PATH=/home/veeratejg/anaconda3/lib:$LD_LIBRARY_PATH' >> ~/.bashrc
source ~/.bashrc
```