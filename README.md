# fpga-image-pack
[![FOSSA Status](https://app.fossa.io/api/projects/git%2Bgithub.com%2Fsanchox%2Ffpga-image-pack.svg?type=shield)](https://app.fossa.io/projects/git%2Bgithub.com%2Fsanchox%2Ffpga-image-pack?ref=badge_shield)


This tool used for packing FPGA binary files (.rbf, .sea, .sed) into one
file called image (.img) to feed it to fpga-manager supported linux driver.

> Now supported only Lattice ECP5 Slave SPI binary images packing.

## Install

```
python3 setup.py install
```
or
```
dpkg -i python3-fpga-image-pack.deb
```

## Build .deb

```
dpkg-buildpackage -A -uc -us
```

## Usage

```
fpga-image-pack-ecp5 [-h] -a FILE -d FILE [-i FILE] [-g GIT_LABEL]
                            [-e EXTRA_INFO] [-v]

Make .img file from .sea and .sed files for ecp5-fpga-mgr driver

optional arguments:
  -h, --help            show this help message and exit
  -v, --verbose         be verbose and show appending info

input files (mandatory):
  binary file's generated by Lattice Diamond

  -a FILE, --algo-file FILE
                        algo file (usually .sea)
  -d FILE, --data-file FILE
                        data file (usually .sed)

ouput files:
  -i FILE, --image-file FILE
                        result image file name (usually .img)

addditional info:
  Additional data appended to image

  -g GIT_LABEL, --git-label GIT_LABEL
                        git label string
  -e EXTRA_INFO, --extra-info EXTRA_INFO
                        extra text info to be appended to img

```

example
```
$ fpga-image-pack-ecp5 -v -a implx_algo.sea -d implx_data.sed -i ecp5_sspi_fw.img -g a042fvfs -e "expiremental"

################################
image packed 2018-06-21 11:36:59.418227
by sanchox@sanchox-metrotek
git description: a042fvfs
algo sha256: e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855
data sha256: 637d7e018332470d48cfdea0746c95bb7ec608175e5e2b3895797bd4026f656b
extra info: expiremental
################################

```

## License

MIT © Aleksandr Gusarov


[![FOSSA Status](https://app.fossa.io/api/projects/git%2Bgithub.com%2Fsanchox%2Ffpga-image-pack.svg?type=large)](https://app.fossa.io/projects/git%2Bgithub.com%2Fsanchox%2Ffpga-image-pack?ref=badge_large)