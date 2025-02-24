project(agl CXX ASM)

add_library(agl OBJECT
  include/agl/aglGPUCommon.hpp
  include/agl/aglGPUMemBlock.hpp

  include/agl/detail/aglGPUMemBlockMgr.h
  include/agl/detail/aglPrivateResource.h

  include/agl/driver/aglGraphicsDriverMgr.h
  include/agl/driver/aglNVNMgr.h

  include/agl/env/aglEnvObj.h
  include/agl/env/aglEnvObjBuffer.h
  include/agl/env/aglEnvObjMgr.h
  include/agl/env/aglEnvObjSetMgr.h
  include/agl/env/aglProjector.h
  include/agl/env/aglFog.h
  include/agl/env/aglLight.h
  include/agl/env/aglProjector.h

  include/agl/g3d/aglNW4FToNN.h

  include/agl/pfx/aglBloom.h
  include/agl/pfx/aglDepthOfField.h
  
  include/agl/texture/aglTextureDataSerializer.h

  include/agl/utl/aglAtomicPtrArray.h
  include/agl/utl/aglParameter.h
  include/agl/utl/aglParameterCurve.hpp
  include/agl/utl/aglParameterIO.h
  include/agl/utl/aglParameterList.h
  include/agl/utl/aglParameterObj.h
  include/agl/utl/aglParameterStringMgr.h
  include/agl/utl/aglResCommon.h
  include/agl/utl/aglResParameter.h
  include/agl/utl/aglScreenShotMgr.h

  src/aglGPUMemBlock.cpp

  src/detail/aglGPUMemBlockMgr.cpp

  src/driver/aglGraphicsDriverMgr.cpp
  src/driver/aglNVNMgr.cpp

  src/utl/aglAtomicPtrArray.cpp
  src/utl/aglParameter.cpp
  src/utl/aglParameterIO.cpp
  src/utl/aglParameterList.cpp
  src/utl/aglParameterObj.cpp
  src/utl/aglParameterStringMgr.cpp
  src/utl/aglResCommon.cpp
  src/utl/aglResParameter.cpp
)

target_compile_options(agl PRIVATE -fno-exceptions)
target_compile_options(agl PRIVATE -fno-strict-aliasing)
target_compile_options(agl PRIVATE -Wno-invalid-offsetof)
target_include_directories(agl PUBLIC include/)

if(NOT TARGET sead)
  add_subdirectory(../sead)
endif()
target_link_libraries(agl PUBLIC sead)
