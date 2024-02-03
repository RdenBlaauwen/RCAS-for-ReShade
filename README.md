# RCAS-for-ReShade

An implementation of AMD FidelityFX RCAS for the ReShade post-processing injector.

RCAS is a light-weight, adaptive sharpening shader included in AMD FidelityFX FSR 1. It is a derivative of AMD FidelityFX CAS, but it "uses a more exact mechanism, solving for the maximum local sharpness possible before clipping." It also lacks the support for scaling that AMD CAS has.

The algorithm applies less sharpening to areas that are already sharp, while more
featureless areas are sharpened more. This prevents artifacts, like ugly contours.

# Features

The defaults are supposed to approximate AMD FidelityFX RCAS to the best of my abilities.
I added some additional features, but these are only available when
ENABLE_NON_STANDARD_FEATURES is set to 1. It can be find among the pre-processor variables.

- The ability to use a Sharpness value of > 1.0, for stronger sharpening than normal.
- Ability to lower the RCAS_LIMIT. This decreases artifacts and extreme sharpening, but may decrease sharpening strength. Lowering this value is recommended when using very high Sharpness settings.
- Option to use green as luma instead of the dot product of luma weights. This improves performance, but may decrease quality.

# Installation

Download the zip file from https://github.com/RdenBlaauwen/RCAS-for-ReShade/archive/refs/heads/main.zip. Then extract it to the `reshade-shaders/Shaders` directory, which is located in the directory that contains the binary of the game in question.

# Credits

Runs on Reshade by Crosire.

This shader is a ReShade port of RCAS. Copyright (C)2023 Advanced Micro Devices, Inc.

- Original file: https://github.com/GPUOpen-LibrariesAndSDKs/FidelityFX-SDK/blob/main/sdk/include/FidelityFX/gpu/fsr1/ffx_fsr1.h
