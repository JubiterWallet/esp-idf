target_include_directories(${COMPONENT_LIB} PUBLIC .)
target_include_directories(${COMPONENT_LIB} PUBLIC private_include)

set(srcs
    "rtc_clk.c"
    "rtc_clk_init.c"
    "rtc_init.c"
    "rtc_pm.c"
    "rtc_sleep.c"
    "rtc_time.c"
    "chip_info.c"
    )

if(NOT BOOTLOADER_BUILD)
    list(APPEND srcs "memprot.c"
                     "esp_hmac.c"
                     "esp_crypto_lock.c"
                     "esp_ds.c")

endif()

add_prefix(srcs "${CMAKE_CURRENT_LIST_DIR}/" "${srcs}")
target_sources(${COMPONENT_LIB} PRIVATE "${srcs}")
