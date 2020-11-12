set(SOURCES
    qcar.cpp
)

set(PUBLIC_HEADERS
    qcomplexlib.h
    qcar.h
)

set(PRIVATE_HEADERS
    qcar_p.h
)

createlib(NAME QComplexLib
    NAMESPACE CC
    VERSION 2.0.0
    SOURCES ${SOURCES}
    PUBLIC_HEADERS ${PUBLIC_HEADERS}
    PRIVATE_HEADERS ${PRIVATE_HEADERS}
    PUBLIC_DEPS CC2::ComplexLib Qt5::Core
    GENERATE_PACKAGE)


add_definitions(-DQCOMPLEXLIB_LIBRARY_BUILD)
# When set to OFF, the library will be built as a static library
if (${BUILD_SHARED_LIBS})
    add_definitions(-DCCQComplexLib_BUILD_SHARED_LIBS)
endif()
