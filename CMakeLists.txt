cmake_minimum_required(VERSION 2.6)
project(packmol Fortran)

# Build for release or debug purposes?
SET(CMAKE_BUILD_TYPE release)
set(CMAKE_Fortran_MODULE_DIRECTORY "${CMAKE_CURRENT_BINARY_DIR}/mod")

add_subdirectory(chemfiles)

# Default flags for release and debug
set(CMAKE_Fortran_FLAGS "${CMAKE_Fortran_FLAGS} -Wall")
set(CMAKE_Fortran_FLAGS_DEBUG "${CMAKE_Fortran_FLAGS_DEBUG} -Werror")

# Build the executable
add_executable(packmol
    cenmass.f90
    gencan.f
    pgencan.f90
    initial.f90
    title.f90
    setsizes.f90
    getinp.f90
    strlength.f90
    output.f90
    checkpoint.f90
    writesuccess.f90
    fparc.f90
    gparc.f90
    gwalls.f90
    comprest.f90
    comparegrad.f90
    packmol.f90
    polartocart.f90
    resetboxes.f90
    tobar.f90
    setijk.f90
    setibox.f90
    restmol.f90
    swaptype.f90
    swaptypemod.f90
    ahestetic.f90
    heuristics.f90
    flashsort.f90
    jacobi.f90
    random.f90
    sizes.f90
    usegencan.f90
    compute_data.f90
    flashmod.f90
    computef.f90
    computeg.f90
    input.f90
)

set_source_files_properties(gencan.f PROPERTIES COMPILE_FLAGS "-Wno-unused-label -Wno-unused-dummy-argument -Wno-maybe-uninitialized")

target_link_libraries(packmol chemfilesf03)

# Installation directive
install (TARGETS packmol DESTINATION bin)
