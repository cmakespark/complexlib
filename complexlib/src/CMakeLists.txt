set(SOURCES
    car.cpp
    trailer/trailer.cpp
)

set(PUBLIC_HEADERS
    complexlib.h
    car.h
    trailer/trailer.h
)

set(PRIVATE_HEADERS
    car_p.h
    trailer/trailer_p.h
)

createlib(NAME ComplexLib
    NAMESPACE CC
    VERSION 2.0.0
    SOURCES ${SOURCES}
    PUBLIC_HEADERS ${PUBLIC_HEADERS}
    PRIVATE_HEADERS ${PRIVATE_HEADERS}
    GENERATE_PACKAGE)

add_definitions(-DCCCOMPLEXLIB_LIBRARY_BUILD)
# When set to OFF, the library will be built as a static library
if (${BUILD_SHARED_LIBS})
    add_definitions(-DCCComplexLib_BUILD_SHARED_LIBS)
endif()
