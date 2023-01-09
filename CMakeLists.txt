aux_source_directory(src RIME_LUA_SRC)
aux_source_directory(src/lib RIME_LUA_LIB_SRC)
aux_source_directory(src/lib/lua RIME_LUA_LIB_LUA_SRC)

add_library(rime-lua-objs OBJECT ${RIME_LUA_SRC} ${RIME_LUA_LIB_SRC} ${RIME_LUA_LIB_LUA_SRC})
if(BUILD_SHARED_LIBS)
  set_target_properties(rime-lua-objs PROPERTIES POSITION_INDEPENDENT_CODE ON)
endif()

set(plugin_name "rime-lua" PARENT_SCOPE)
set(plugin_objs $<TARGET_OBJECTS:rime-lua-objs> PARENT_SCOPE)
set(plugin_deps ${LUA_TARGET} ${rime_library} ${rime_gears_library} PARENT_SCOPE)
set(plugin_modules "lua" PARENT_SCOPE)
