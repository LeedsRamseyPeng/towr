# Must be shared due to LGPL.
add_library(qpOASES SHARED
  src/BLASReplacement.cpp
  src/Bounds.cpp
  src/Constraints.cpp
  src/Flipper.cpp
  src/Indexlist.cpp
  src/LAPACKReplacement.cpp
  src/Makefile
  src/Matrices.cpp
  src/MessageHandling.cpp
  src/Options.cpp
  src/OQPinterface.cpp
  src/QProblemB.cpp
  src/QProblem.cpp
  src/SolutionAnalysis.cpp
  src/SparseSolver.cpp
  src/SQProblem.cpp
  src/SQProblemSchur.cpp
  src/SubjectTo.cpp
  src/Utils.cpp
)
target_include_directories(qpOASES
  SYSTEM PUBLIC
    ${PENGUIN_INCLUDE_DIR}/third_party/qpOASES/include
)
target_include_directories(qpOASES
  PUBLIC
    ${PENGUIN_INCLUDE_DIR}
)
if(CMAKE_CXX_COMPILER_ID STREQUAL "GNU")
  target_compile_options(qpOASES
    PRIVATE
      -Wno-format-truncation
  )
elseif(CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  target_compile_options(qpOASES
    PRIVATE
      -Wno-empty-body
  )
endif()
target_compile_definitions(qpOASES
  PRIVATE
    __NO_COPYRIGHT__
)
# install(TARGETS qpOASES)
