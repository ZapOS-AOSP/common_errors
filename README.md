# Common Errors occurred while Building ZapOS
## A list of common errors with fixes 
----------------------------------------------------------------------------

## First Error 
``` prebuilts/clang/host/linux-x86/clang-r475365b/lib/clang/16.0.2/include/arm_acle.h:615:10: error: '__builtin_arm_crc32cb' needs target feature crc
  return __builtin_arm_crc32cb(__a, __b); 
  ```
  
## FIX
----------------------------------------------------------------------------
### In your **BoardConfig.mk** , under CPU arch flags You must have these - 

``` TARGET_CPU_VARIANT := generic
    TARGET_2ND_CPU_VARIANT := generic 
```

### So Fix it , just remove the ``` generic ``` and add whatever value is in ```TARGET_CPU_VARIANT_RUNTIME``` and ```TARGET_2ND_CPU_VARIANT_RUNTIME```
## For Example : If your Flags are like this :

``` # Architecture
TARGET_ARCH := arm64
TARGET_ARCH_VARIANT := armv8-2a-dotprod
TARGET_CPU_ABI := arm64-v8a
TARGET_CPU_ABI2 :=
TARGET_CPU_VARIANT := generic
TARGET_2ND_CPU_VARIANT_RUNTIME := cortex-a76

TARGET_2ND_ARCH := arm
TARGET_2ND_ARCH_VARIANT := armv8-2a
TARGET_2ND_CPU_ABI := armeabi-v7a
TARGET_2ND_CPU_ABI2 := armeabi
TARGET_2ND_CPU_VARIANT := generic
TARGET_2ND_CPU_VARIANT_RUNTIME := cortex-a55
``` 

## Then change it to : 

``` # Architecture
TARGET_ARCH := arm64
TARGET_ARCH_VARIANT := armv8-2a-dotprod
TARGET_CPU_ABI := arm64-v8a
TARGET_CPU_ABI2 :=
TARGET_CPU_VARIANT := cortex-a76
TARGET_2ND_CPU_VARIANT_RUNTIME := cortex-a76

TARGET_2ND_ARCH := arm
TARGET_2ND_ARCH_VARIANT := armv8-2a
TARGET_2ND_CPU_ABI := armeabi-v7a
TARGET_2ND_CPU_ABI2 := armeabi
TARGET_2ND_CPU_VARIANT := cortex-a55
TARGET_2ND_CPU_VARIANT_RUNTIME := cortex-a55
```

----------------------------------------------------------------------------
