# cmake-dependency-scan pkg:github/STMicroelectronics/STM32CubeWB@9c2f0efe94efd420f9810108e303a9e9cf500802#Middlewares/ST/STM32_WPAN

add_library(hal_st.stm32_wpan_stm32wbxx STATIC)
emil_build_for(hal_st.stm32_wpan_stm32wbxx TARGET_MCU_FAMILY stm32wbxx PREREQUISITE_BOOL HALST_STANDALONE)

target_include_directories(hal_st.stm32_wpan_stm32wbxx PUBLIC
    "$<BUILD_INTERFACE:${CMAKE_CURRENT_LIST_DIR}>"
    "$<BUILD_INTERFACE:${CMAKE_CURRENT_LIST_DIR}/app_specific>"
    "$<BUILD_INTERFACE:${CMAKE_CURRENT_LIST_DIR}/ble>"
    "$<BUILD_INTERFACE:${CMAKE_CURRENT_LIST_DIR}/ble/core>"
    "$<BUILD_INTERFACE:${CMAKE_CURRENT_LIST_DIR}/ble/core/auto>"
    "$<BUILD_INTERFACE:${CMAKE_CURRENT_LIST_DIR}/ble/core/template>"
    "$<BUILD_INTERFACE:${CMAKE_CURRENT_LIST_DIR}/interface/patterns/ble_thread>"
    "$<BUILD_INTERFACE:${CMAKE_CURRENT_LIST_DIR}/interface/patterns/ble_thread/shci>"
    "$<BUILD_INTERFACE:${CMAKE_CURRENT_LIST_DIR}/interface/patterns/ble_thread/tl>"
    "$<BUILD_INTERFACE:${CMAKE_CURRENT_LIST_DIR}/utilities>"
    "$<INSTALL_INTERFACE:${CMAKE_INSTALL_INCLUDEDIR}>"
)

target_link_libraries(hal_st.stm32_wpan_stm32wbxx PUBLIC
    st.hal_driver
)

target_sources(hal_st.stm32_wpan_stm32wbxx PRIVATE
    ble/core/auto/ble_gap_aci.c
    ble/core/auto/ble_gap_aci.h
    ble/core/auto/ble_gatt_aci.c
    ble/core/auto/ble_gatt_aci.h
    ble/core/auto/ble_hal_aci.c
    ble/core/auto/ble_hal_aci.h
    ble/core/auto/ble_hci_le.c
    ble/core/auto/ble_hci_le.h
    ble/core/auto/ble_l2cap_aci.c
    ble/core/auto/ble_l2cap_aci.h
    ble/core/template/osal.c
    ble/core/template/osal.h
    ble/svc/Src/bls.c
    ble/svc/Src/svc_ctl.c
    interface/patterns/ble_thread/shci/shci.c
    interface/patterns/ble_thread/shci/shci.h
    interface/patterns/ble_thread/tl/hci_tl.c
    interface/patterns/ble_thread/tl/hci_tl.h
    interface/patterns/ble_thread/tl/hci_tl_if.c
    interface/patterns/ble_thread/tl/shci_tl.c
    interface/patterns/ble_thread/tl/shci_tl.h
    interface/patterns/ble_thread/tl/shci_tl_if.c
    interface/patterns/ble_thread/tl/tl_mbox.c
    interface/patterns/ble_thread/tl/tl.h

    #Init workaround
    utilities/otp.c
    utilities/stm_list.c
    utilities/dbg_trace.c
    utilities/stm_queue.c
    app_specific/target/hw_ipcc.c
)
