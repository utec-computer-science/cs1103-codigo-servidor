# cs1103-codigo-servidor

## Make deb package

```
mkdir -p build && cd build
cmake -DCMAKE_INSTALL_PREFIX=/usr ..
make -j$(nproc) package
```
