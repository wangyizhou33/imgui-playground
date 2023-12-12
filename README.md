    ```sh
        pip install conan
        # source ~/.profile
        # install cmake 3.15.7 (cmake 3.14 is too old)
        conan install . --output-folder=build --build=missing -c tools.system.package_manager:mode=install -c tools.system.package_manager:sudo=true        # a lot of cmake files are generated in the build folder
        cd build
        cmake .. -DCMAKE_TOOLCHAIN_FILE=conan_toolchain.cmake -DCMAKE_BUILD_TYPE=Release
        cmake --build . --config Release
        ./test_package
    ```