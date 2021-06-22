# Solar ![Build Status](https://github.com/madmann91/solar/workflows/build-and-test/badge.svg)

> SoL currently relies on modern C++ features and those are not supported by GitHub CI (yet).
> Therefore, the build status above is expected to fail, at least for now (as of 2021-06-22).

This is a meta-repository that pulls SoL and all its dependencies, and builds it automatically.
In order to build SoL, just use the following command:

    mkdir build
    cd build
    ccmake .. -DCMAKE_BUILD_TYPE=<Debug|Release|RelWithDebInfo>
    cmake --build .
