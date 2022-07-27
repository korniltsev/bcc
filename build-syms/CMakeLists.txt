
set(bcc_syms_sources ../src/cc/bcc_syms.cc ../src/cc/bcc_elf.c ../src/cc/bcc_perf_map.c ../src/cc/bcc_proc.c ../src/cc/common.cc)

add_library(bcc-syms-static STATIC ${bcc_syms_sources} )
target_link_libraries(bcc-syms-static elf z)
set_target_properties(bcc-syms-static  PROPERTIES OUTPUT_NAME bcc-syms)

add_library(bcc-syms SHARED ${bcc_syms_sources})
target_link_libraries(bcc-syms elf z)


install(TARGETS bcc-syms bcc-syms-static DESTINATION )
install(FILES ../src/cc/bcc_syms.h ../src/cc/bcc_proc.h DESTINATION include/bcc_syms)