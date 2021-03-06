if(SWIFT_BUILD_STDLIB OR SWIFT_BUILD_SDK_OVERLAY)
  add_subdirectory(SwiftPrivate)
endif()

if(CMAKE_SYSTEM_NAME STREQUAL "Darwin")
  if(SWIFT_BUILD_SDK_OVERLAY)
    # FIXME: there is nothing Darwin-specific in StdlibUnittest, but to use
    # POSIX APIs it imports the Darwin module on Apple platforms, so it can't
    # be built separately from the SDK overlay.
    add_subdirectory(StdlibUnittest)
    add_subdirectory(StdlibCollectionUnittest)
    add_subdirectory(StdlibUnittestFoundationExtras)
    add_subdirectory(SwiftPrivateLibcExtras)
    add_subdirectory(SwiftPrivatePthreadExtras)
    add_subdirectory(SwiftReflectionTest)
  endif()
endif()

if(CMAKE_SYSTEM_NAME STREQUAL "Linux" OR CMAKE_SYSTEM_NAME STREQUAL "FreeBSD")
  add_subdirectory(StdlibUnittest)
  add_subdirectory(StdlibCollectionUnittest)
  add_subdirectory(SwiftPrivateLibcExtras)
  add_subdirectory(SwiftPrivatePthreadExtras)
endif()
