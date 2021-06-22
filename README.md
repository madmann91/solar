# Solar ![Build Status](https://github.com/madmann91/bvh/workflows/build-and-test/badge.svg)

Meta-repository that pulls SoL and all its dependencies, and builds it automatically.
In order to build SoL, just use the following command:

    mkdir build
    cd build
    ccmake .. -DCMAKE_BUILD_TYPE=<Debug|Release|RelWithDebInfo>
    cmake --build .
