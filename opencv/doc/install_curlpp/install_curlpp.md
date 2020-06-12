# install curlpp

## step 1 install curl
```bash
sudo apt-get install  curl # install curl
```
## step 2 download curlpp

```bash
git clone https://github.com/jpbarrette/curlpp.git
```

## step 3 compile and install
```
cd curlpp
mkdir build
cd build
cmake ../
make
make install
```

## tip
compile option  is -lcrul -lcrulpp 
