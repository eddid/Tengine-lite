include_directories(
  include
  3rd/hcl/include
  src/dev/include
  )

set(TENGINE_INC
    include/tengine_c_api.h
)

set(TENGINE_SRC
    src/dev/cpu/cpu_device.c
    src/dev/cpu/cpu_module.c
    src/dev/cpu/cpu_node_ops.c
    src/dev/cpu/cpu_probe.c
    src/dev/cpu/hcl_cpu.c
    src/dev/cpu/hcl_module.c
    src/dev/cpu/op/conv/conv_cmsis.c
    src/dev/cpu/op/conv/conv_hcl.c
    src/dev/cpu/op/fc/fc_cmsis.c
    src/dev/cpu/op/fc/fc_hcl.c
    src/dev/cpu/op/pooling/pooling_cmsis.c
    src/dev/cpu/op/pooling/pooling_hcl.c
    src/dev/cpu/op/relu/relu_cmsis.c
    src/dev/cpu/op/softmax/softmax_cmsis.c
    src/lib/buddy_mem.c
    src/lib/buddy_mem_init.c
    src/lib/dev_allocator.c
    src/lib/exec_scheduler.c
    src/lib/hash.c
    src/lib/hash_impl.c
    src/lib/map.c
    src/lib/mem_stat.c
    src/lib/module.c
    src/lib/nn_device.c
    src/lib/sys_port.c
    src/lib/tengine_c_api.c
    src/lib/tengine_errno.c
    src/lib/tengine_exec.c
    src/lib/tengine_ir.c
    src/lib/tengine_log.c
    src/lib/tengine_op.c
    src/lib/tengine_serializer.c
    src/lib/tengine_utils.c
    src/lib/vector.c
    src/op/convolution.c
    src/op/fc.c
    src/op/pooling.c
    src/op/simple_op.c
)

set(TENGINE_TINY
    tests/bin/tiny/test_tiny.c
    tests/bin/tiny/tiny_graph_generated.c
)

add_library(tengine STATIC ${TENGINE_SRC})
source_group("include" FILES ${TENGINE_INC})
source_group("src" FILES ${TENGINE_SRC})
add_target_properties(tengine COMPILE_FLAGS "/TP -DCONFIG_ARCH_CORTEX_M -Dinline=")
target_link_libraries(tengine ${libs})

link_directories(${PORTING_LINKPATH})
add_executable(tengine_tiny ${TENGINE_TINY})
source_group("src" FILES ${TENGINE_TINY})
add_target_properties(tengine_tiny COMPILE_FLAGS "/TP -DCONFIG_ARCH_CORTEX_M -Dinline=")
target_link_libraries(tengine_tiny porting tengine)