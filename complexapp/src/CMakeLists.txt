set(SOURCES
    main.cpp
)

set(HEADERS
)

createapp(NAME ComplexApp
    VERSION 2.0.0
    CONSOLE
    SOURCES ${SOURCES}
    HEADERS ${HEADERS}
    DEPS CC2::ComplexLib)
