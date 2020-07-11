# cs1103-codigo-servidor

## Make deb package

```
mkdir -p build && cd build
cmake ..
make -j$(nproc) package
```
