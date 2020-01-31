# Pytorch augmnetations

GPU augmentations realization using pytorch.

There you can find benchmark results.

## Table of contents

- [GPU faster then CPU including transfer](#gpu-faster-then-cpu-including-transfer)
    - [Faster: Pixel level](#faster-pixel-level1)
    - [Faster: Spatial](#faster-spatial1)
- [GPU faster then CPU without transfer](#gpu-faster-then-cpu-without-transfer)
    - [Faster: Pixel level](#faster-pixel-level2)
    - [Faster: Spatial](#faster-spatial2)
- [Pixel level](#pixel-level)
- [Spatial](#spatial)

## GPU faster then CPU including transfer

There you can find links to transforms that is faster then CPU implementations
including time to move tensor to device.

### Faster: Pixel level

- [ISONoise](#isonoise)

### Faster: Spatial


## GPU faster then CPU without transfer

There you can find links to transforms that is faster then CPU implementations
without time to move tensor to device.

### Faster: Pixel level

- [ISONoise](#isonoise)
- [Normalize](#normalize)
- [RGBShift](#rgbshift)
- [RandomBrightnessContrast](#randombrightnesscontrast)
- [RandomGamma](#randomgamma)

### Faster: Spatial

- [HorizontalFlip](#horizontalflip)
- [LongestMaxSize](#longestmaxsize)
- [PadIfNeeded](#padifneeded)
- [RandomRotate90](#randomrotate90)
- [RandomScale](#randomscale)
- [RandomSizedCrop](#randomsizedcrop)
- [Resize](#resize)
- [SmallestMaxSize](#smallestmaxsize)

## Pixel level

### Blur

|          Shapes |  CPU FPS |    GPU with ToTensorV2 FPS | GPU without ToTensorV2 FPS |
| --------------- | -------- | -------------------------- | ----------------------- |
| [1024, 1024, 3] |   554.56 |                     211.58 |                  532.50 |
|   [512, 512, 3] |  2199.19 |                     989.08 |                 2161.42 |
|   [256, 256, 3] |  7806.46 |                    2827.89 |                 5565.17 |
|   [128, 128, 3] | 21055.21 |                    3789.57 |                 8213.43 |

### ChannelDropout

|          Shapes |  CPU FPS |    GPU with ToTensorV2 FPS | GPU without ToTensorV2 FPS |
| --------------- | -------- | -------------------------- | ----------------------- |
| [1024, 1024, 3] |  1723.74 |                     321.70 |                 6585.29 |
|   [512, 512, 3] |  5243.80 |                    1881.08 |                 8989.66 |
|   [256, 256, 3] | 17706.90 |                    3916.78 |                10207.38 |
|   [128, 128, 3] | 28345.45 |                    5998.54 |                11028.12 |

### ChannelShuffle

|          Shapes |  CPU FPS |    GPU with ToTensorV2 FPS | GPU without ToTensorV2 FPS |
| --------------- | -------- | -------------------------- | ----------------------- |
| [1024, 1024, 3] |  1184.03 |                     346.11 |                 8007.30 |
|   [512, 512, 3] |  4182.43 |                    2002.15 |                13250.47 |
|   [256, 256, 3] | 12958.38 |                    4568.30 |                17541.76 |
|   [128, 128, 3] | 28956.79 |                    7510.74 |                17432.54 |

### CoarseDropout

|          Shapes |  CPU FPS |    GPU with ToTensorV2 FPS | GPU without ToTensorV2 FPS |
| --------------- | -------- | -------------------------- | ----------------------- |
| [1024, 1024, 3] |  6554.73 |                     322.86 |                 4683.55 |
|   [512, 512, 3] | 14015.59 |                    1510.27 |                 4664.02 |
|   [256, 256, 3] | 20067.67 |                    2624.83 |                 4595.96 |
|   [128, 128, 3] | 22107.51 |                    3087.01 |                 4592.17 |

### Downscale

|          Shapes |  CPU FPS |    GPU with ToTensorV2 FPS | GPU without ToTensorV2 FPS |
| --------------- | -------- | -------------------------- | ----------------------- |
| [1024, 1024, 3] |  2896.42 |                     331.32 |                 5189.17 |
|   [512, 512, 3] |  7703.04 |                    1775.47 |                10814.52 |
|   [256, 256, 3] | 10499.49 |                    3827.65 |                11214.93 |
|   [128, 128, 3] | 25015.68 |                    5950.53 |                11605.42 |

### FromFloat

|          Shapes |  CPU FPS |    GPU with ToTensorV2 FPS | GPU without ToTensorV2 FPS |
| --------------- | -------- | -------------------------- | ----------------------- |
| [1024, 1024, 3] |   790.76 |                     349.48 |                 6738.92 |
|   [512, 512, 3] |  5643.50 |                    1879.51 |                16469.56 |
|   [256, 256, 3] | 19358.12 |                    4962.88 |                23232.77 |
|   [128, 128, 3] | 40642.87 |                    8518.12 |                23122.23 |

### GaussianBlur

|          Shapes |  CPU FPS |    GPU with ToTensorV2 FPS | GPU without ToTensorV2 FPS |
| --------------- | -------- | -------------------------- | ----------------------- |
| [1024, 1024, 3] |  1310.98 |                     233.37 |                  635.92 |
|   [512, 512, 3] |  3551.21 |                    1110.59 |                 2495.08 |
|   [256, 256, 3] | 12021.09 |                    3037.62 |                 6109.36 |
|   [128, 128, 3] | 19858.27 |                    5307.51 |                 9659.35 |

### HueSaturationValue

|          Shapes | CPU FPS |    GPU with ToTensorV2 FPS | GPU without ToTensorV2 FPS |
| --------------- | ------- | -------------------------- | ----------------------- |
| [1024, 1024, 3] |  312.11 |                     161.70 |                  314.94 |
|   [512, 512, 3] |  971.48 |                     621.00 |                  860.10 |
|   [256, 256, 3] | 1713.63 |                     752.76 |                  943.47 |
|   [128, 128, 3] | 4863.41 |                     808.52 |                  952.43 |

### ISONoise

|          Shapes | CPU FPS |    GPU with ToTensorV2 FPS | GPU without ToTensorV2 FPS |
| --------------- | ------- | -------------------------- | ----------------------- |
| [1024, 1024, 3] |    6.64 |                     181.49 |                  427.95 |
|   [512, 512, 3] |   26.55 |                     696.79 |                 1088.19 |
|   [256, 256, 3] |  105.66 |                     921.39 |                 1121.29 |
|   [128, 128, 3] |  395.15 |                     999.43 |                 1132.37 |

### InvertImg

|          Shapes |  CPU FPS |    GPU with ToTensorV2 FPS | GPU without ToTensorV2 FPS |
| --------------- | -------- | -------------------------- | ----------------------- |
| [1024, 1024, 3] |  6120.57 |                     340.66 |                10168.75 |
|   [512, 512, 3] | 22487.15 |                    1881.96 |                21719.77 |
|   [256, 256, 3] | 48323.14 |                    4882.67 |                27643.39 |
|   [128, 128, 3] | 65570.83 |                    9103.03 |                28860.75 |

### MedianBlur

|          Shapes | CPU FPS |    GPU with ToTensorV2 FPS | GPU without ToTensorV2 FPS |
| --------------- | ------- | -------------------------- | ----------------------- |
| [1024, 1024, 3] |   28.24 |                      14.97 |                   16.29 |
|   [512, 512, 3] |  101.54 |                      58.02 |                   64.31 |
|   [256, 256, 3] |  385.39 |                     234.30 |                  239.44 |
|   [128, 128, 3] | 1469.66 |                     825.22 |                  922.98 |

### MotionBlur

|          Shapes |  CPU FPS |    GPU with ToTensorV2 FPS | GPU without ToTensorV2 FPS |
| --------------- | -------- | -------------------------- | ----------------------- |
| [1024, 1024, 3] |   565.94 |                     214.96 |                  576.34 |
|   [512, 512, 3] |  1975.16 |                     928.42 |                 1932.38 |
|   [256, 256, 3] |  6435.16 |                    2388.28 |                 4475.73 |
|   [128, 128, 3] | 12962.67 |                    3738.80 |                 5921.68 |

### Normalize

|          Shapes | CPU FPS |    GPU with ToTensorV2 FPS | GPU without ToTensorV2 FPS |
| --------------- | ------- | -------------------------- | ----------------------- |
| [1024, 1024, 3] |  119.63 |                    1161.12 |                 4845.38 |
|   [512, 512, 3] |  556.09 |                    2895.42 |                11973.46 |
|   [256, 256, 3] | 2162.43 |                    5389.02 |                12169.96 |
|   [128, 128, 3] | 7476.34 |                    7399.87 |                12317.68 |

### RGBShift

|          Shapes | CPU FPS |    GPU with ToTensorV2 FPS | GPU without ToTensorV2 FPS |
| --------------- | ------- | -------------------------- | ----------------------- |
| [1024, 1024, 3] |  375.73 |                     315.14 |                 3902.95 |
|   [512, 512, 3] | 1237.67 |                    1475.15 |                 6533.39 |
|   [256, 256, 3] | 3161.64 |                    3212.71 |                 7226.45 |
|   [128, 128, 3] | 6479.90 |                    4202.85 |                 7106.11 |

### RandomBrightnessContrast

|          Shapes |  CPU FPS |    GPU with ToTensorV2 FPS | GPU without ToTensorV2 FPS |
| --------------- | -------- | -------------------------- | ----------------------- |
| [1024, 1024, 3] |  2102.40 |                     322.45 |                 4342.69 |
|   [512, 512, 3] |  5169.41 |                    1963.00 |                14396.10 |
|   [256, 256, 3] |  7104.69 |                    4442.74 |                15816.52 |
|   [128, 128, 3] | 13983.06 |                    7011.38 |                16653.98 |

### RandomGamma

|          Shapes |  CPU FPS |    GPU with ToTensorV2 FPS | GPU without ToTensorV2 FPS |
| --------------- | -------- | -------------------------- | ----------------------- |
| [1024, 1024, 3] |  1670.61 |                     329.52 |                 5342.93 |
|   [512, 512, 3] |  3358.34 |                    1786.90 |                12912.70 |
|   [256, 256, 3] |  7684.61 |                    4603.82 |                23190.25 |
|   [128, 128, 3] | 16283.37 |                    8279.27 |                23281.12 |

### RandomSnow

|          Shapes | CPU FPS |    GPU with ToTensorV2 FPS | GPU without ToTensorV2 FPS |
| --------------- | ------- | -------------------------- | ----------------------- |
| [1024, 1024, 3] |   57.59 |                     183.25 |                  398.64 |
|   [512, 512, 3] |  224.75 |                     651.47 |                  972.05 |
|   [256, 256, 3] |  768.38 |                     898.66 |                 1088.01 |
|   [128, 128, 3] | 2662.55 |                     943.85 |                 1110.32 |

### Solarize

|          Shapes |  CPU FPS |    GPU with ToTensorV2 FPS | GPU without ToTensorV2 FPS |
| --------------- | -------- | -------------------------- | ----------------------- |
| [1024, 1024, 3] |  1988.61 |                     321.43 |                 4462.45 |
|   [512, 512, 3] |  5655.52 |                    1793.41 |                11460.47 |
|   [256, 256, 3] |  6685.79 |                    4512.09 |                15233.24 |
|   [128, 128, 3] | 15293.06 |                    7176.96 |                15121.80 |

### ToFloat

|          Shapes |  CPU FPS |    GPU with ToTensorV2 FPS | GPU without ToTensorV2 FPS |
| --------------- | -------- | -------------------------- | ----------------------- |
| [1024, 1024, 3] |   646.68 |                     335.46 |                10380.91 |
|   [512, 512, 3] |  3522.55 |                    2032.73 |                20331.09 |
|   [256, 256, 3] | 11821.20 |                    5255.59 |                29495.39 |
|   [128, 128, 3] | 31255.99 |                    9265.33 |                30930.30 |

### ToGray

|          Shapes |  CPU FPS |    GPU with ToTensorV2 FPS | GPU without ToTensorV2 FPS |
| --------------- | -------- | -------------------------- | ----------------------- |
| [1024, 1024, 3] |  5459.70 |                     332.38 |                 8635.94 |
|   [512, 512, 3] | 15072.24 |                    1738.90 |                14879.75 |
|   [256, 256, 3] | 23078.98 |                    4240.34 |                18788.57 |
|   [128, 128, 3] | 47304.00 |                    7786.61 |                18788.49 |


## Spatial

### CenterCrop

|          Shapes |  CPU FPS |    GPU with ToTensorV2 FPS | GPU without ToTensorV2 FPS |
| --------------- | -------- | -------------------------- | ----------------------- |
| [1024, 1024, 3] | 78795.87 |                     311.42 |                47259.76 |
|   [512, 512, 3] | 61981.73 |                    1718.29 |                59841.69 |
|   [256, 256, 3] | 81389.06 |                    5196.67 |                58459.64 |
|   [128, 128, 3] | 96859.43 |                   10675.49 |                63331.28 |

### Crop

|          Shapes |  CPU FPS |    GPU with ToTensorV2 FPS | GPU without ToTensorV2 FPS |
| --------------- | -------- | -------------------------- | ----------------------- |
| [1024, 1024, 3] | 55938.97 |                     339.24 |                48556.43 |
|   [512, 512, 3] | 85042.66 |                    1915.59 |                58950.16 |
|   [256, 256, 3] | 78960.52 |                    5409.51 |                62743.90 |
|   [128, 128, 3] | 80944.55 |                   10091.95 |                58836.05 |

### CropNonEmptyMaskIfExists

|          Shapes | CPU FPS |    GPU with ToTensorV2 FPS | GPU without ToTensorV2 FPS |
| --------------- | ------- | -------------------------- | ----------------------- |
| [1024, 1024, 3] |   87.23 |                     222.92 |                 1245.96 |
|   [512, 512, 3] |  348.45 |                     699.99 |                 1551.11 |
|   [256, 256, 3] | 1304.37 |                    1198.90 |                 1735.06 |
|   [128, 128, 3] | 3652.16 |                    1404.01 |                 1769.30 |

### Flip

|          Shapes |  CPU FPS |    GPU with ToTensorV2 FPS | GPU without ToTensorV2 FPS |
| --------------- | -------- | -------------------------- | ----------------------- |
| [1024, 1024, 3] |  1068.19 |                     317.37 |                 5186.67 |
|   [512, 512, 3] |  4350.04 |                    1521.80 |                12654.03 |
|   [256, 256, 3] | 13900.71 |                    4384.31 |                17654.65 |
|   [128, 128, 3] | 38224.21 |                    7226.34 |                18361.36 |

### GridDistortion

|          Shapes | CPU FPS |    GPU with ToTensorV2 FPS | GPU without ToTensorV2 FPS |
| --------------- | ------- | -------------------------- | ----------------------- |
| [1024, 1024, 3] |  280.89 |                     129.21 |                  240.99 |
|   [512, 512, 3] |  762.70 |                     531.91 |                  925.63 |
|   [256, 256, 3] | 1440.29 |                    1303.62 |                 1836.91 |
|   [128, 128, 3] | 2227.03 |                    1698.66 |                 2082.59 |

### HorizontalFlip

|          Shapes |  CPU FPS |    GPU with ToTensorV2 FPS | GPU without ToTensorV2 FPS |
| --------------- | -------- | -------------------------- | ----------------------- |
| [1024, 1024, 3] |   907.56 |                     339.50 |                11555.83 |
|   [512, 512, 3] |  3508.20 |                    1981.36 |                26379.27 |
|   [256, 256, 3] | 11345.09 |                    5357.10 |                44042.55 |
|   [128, 128, 3] | 29734.18 |                   10209.12 |                44184.52 |

### LongestMaxSize

|          Shapes |  CPU FPS |    GPU with ToTensorV2 FPS | GPU without ToTensorV2 FPS |
| --------------- | -------- | -------------------------- | ----------------------- |
| [1024, 1024, 3] | 78310.38 |                     374.83 |                83635.17 |
|   [512, 512, 3] |  1761.37 |                    1573.69 |                 7138.51 |
|   [256, 256, 3] |  2525.59 |                    3670.57 |                 8205.06 |
|   [128, 128, 3] |  3378.55 |                    5538.06 |                 8366.82 |

### OpticalDistortion

|          Shapes | CPU FPS |    GPU with ToTensorV2 FPS | GPU without ToTensorV2 FPS |
| --------------- | ------- | -------------------------- | ----------------------- |
| [1024, 1024, 3] |  332.01 |                     102.84 |                  210.20 |
|   [512, 512, 3] | 1110.42 |                     388.62 |                 1014.19 |
|   [256, 256, 3] | 1865.03 |                    1203.56 |                 3128.77 |
|   [128, 128, 3] | 5888.09 |                    2076.48 |                 5930.09 |

### PadIfNeeded

|          Shapes | CPU FPS |    GPU with ToTensorV2 FPS | GPU without ToTensorV2 FPS |
| --------------- | ------- | -------------------------- | ----------------------- |
| [1024, 1024, 3] | 6354.81 |                     329.09 |                 8114.34 |
|   [512, 512, 3] | 2341.09 |                    1571.97 |                 7569.99 |
|   [256, 256, 3] | 3023.69 |                    2727.72 |                 5200.01 |
|   [128, 128, 3] | 4038.92 |                    3787.36 |                 5661.85 |

### RandomCrop

|          Shapes |  CPU FPS |    GPU with ToTensorV2 FPS | GPU without ToTensorV2 FPS |
| --------------- | -------- | -------------------------- | ----------------------- |
| [1024, 1024, 3] | 73674.76 |                     348.91 |                45324.23 |
|   [512, 512, 3] | 67454.23 |                    2031.04 |                51482.80 |
|   [256, 256, 3] | 90525.20 |                    5423.73 |                59514.78 |
|   [128, 128, 3] | 82449.80 |                   10097.63 |                52684.98 |

### RandomCropNearBBox

|          Shapes |  CPU FPS |    GPU with ToTensorV2 FPS | GPU without ToTensorV2 FPS |
| --------------- | -------- | -------------------------- | ----------------------- |
| [1024, 1024, 3] | 48349.33 |                     338.45 |                37755.91 |
|   [512, 512, 3] | 49455.30 |                    1999.41 |                39383.14 |
|   [256, 256, 3] | 54046.13 |                    5159.27 |                41891.93 |
|   [128, 128, 3] | 54224.30 |                    7944.72 |                42438.29 |

### RandomGridShuffle

|          Shapes | CPU FPS |    GPU with ToTensorV2 FPS | GPU without ToTensorV2 FPS |
| --------------- | ------- | -------------------------- | ----------------------- |
| [1024, 1024, 3] | 1280.14 |                     224.16 |                 1508.77 |
|   [512, 512, 3] | 1720.99 |                     731.33 |                 1521.58 |
|   [256, 256, 3] | 1919.64 |                    1158.17 |                 1524.95 |
|   [128, 128, 3] | 2034.17 |                    1241.84 |                 1543.19 |

### RandomResizedCrop

|          Shapes |  CPU FPS |    GPU with ToTensorV2 FPS | GPU without ToTensorV2 FPS |
| --------------- | -------- | -------------------------- | ----------------------- |
| [1024, 1024, 3] |  9470.73 |                     352.24 |                14990.90 |
|   [512, 512, 3] |  9752.83 |                    1922.41 |                14440.21 |
|   [256, 256, 3] | 11810.12 |                    4411.08 |                15411.34 |
|   [128, 128, 3] | 16674.63 |                    6660.89 |                13969.09 |

### RandomRotate90

|          Shapes |  CPU FPS |    GPU with ToTensorV2 FPS | GPU without ToTensorV2 FPS |
| --------------- | -------- | -------------------------- | ----------------------- |
| [1024, 1024, 3] |   289.38 |                     309.80 |                 4496.37 |
|   [512, 512, 3] |  1347.10 |                    1608.50 |                10232.76 |
|   [256, 256, 3] |  4826.26 |                    4364.23 |                16781.91 |
|   [128, 128, 3] | 12895.12 |                    7286.33 |                18067.37 |

### RandomScale

|          Shapes |  CPU FPS |    GPU with ToTensorV2 FPS | GPU without ToTensorV2 FPS |
| --------------- | -------- | -------------------------- | ----------------------- |
| [1024, 1024, 3] |  1054.67 |                     321.12 |                 6590.26 |
|   [512, 512, 3] |  1891.75 |                    1965.15 |                14460.62 |
|   [256, 256, 3] |  4116.70 |                    4645.68 |                19503.95 |
|   [128, 128, 3] | 12570.14 |                    7687.61 |                19572.75 |

### RandomSizedBBoxSafeCrop

|          Shapes | CPU FPS |    GPU with ToTensorV2 FPS | GPU without ToTensorV2 FPS |
| --------------- | ------- | -------------------------- | ----------------------- |
| [1024, 1024, 3] |  324.56 |                     126.48 |                  318.59 |
|   [512, 512, 3] |  361.56 |                     215.01 |                  361.62 |
|   [256, 256, 3] |  191.70 |                    1581.22 |                  198.25 |
|   [128, 128, 3] |  485.77 |                    1580.72 |                  485.61 |

### RandomSizedCrop

|          Shapes |  CPU FPS |    GPU with ToTensorV2 FPS | GPU without ToTensorV2 FPS |
| --------------- | -------- | -------------------------- | ----------------------- |
| [1024, 1024, 3] | 12069.59 |                     335.98 |                14689.02 |
|   [512, 512, 3] | 12848.23 |                    1675.72 |                14591.93 |
|   [256, 256, 3] | 13272.74 |                    4192.66 |                15274.34 |
|   [128, 128, 3] | 12975.22 |                    6553.13 |                15270.34 |

### Resize

|          Shapes |  CPU FPS |    GPU with ToTensorV2 FPS | GPU without ToTensorV2 FPS |
| --------------- | -------- | -------------------------- | ----------------------- |
| [1024, 1024, 3] | 10573.52 |                     342.41 |                20473.00 |
|   [512, 512, 3] | 10685.31 |                    1543.02 |                21126.80 |
|   [256, 256, 3] | 11099.83 |                    4672.40 |                21346.47 |
|   [128, 128, 3] | 15652.43 |                    7555.04 |                21268.43 |

### Rotate

|          Shapes | CPU FPS |    GPU with ToTensorV2 FPS | GPU without ToTensorV2 FPS |
| --------------- | ------- | -------------------------- | ----------------------- |
| [1024, 1024, 3] |  550.59 |                      58.30 |                   80.06 |
|   [512, 512, 3] | 1060.63 |                     268.04 |                  339.30 |
|   [256, 256, 3] | 2249.47 |                     645.30 |                  728.21 |
|   [128, 128, 3] | 6969.90 |                     820.78 |                  883.94 |

### ShiftScaleRotate

|          Shapes | CPU FPS |    GPU with ToTensorV2 FPS | GPU without ToTensorV2 FPS |
| --------------- | ------- | -------------------------- | ----------------------- |
| [1024, 1024, 3] |  534.01 |                      62.83 |                   74.39 |
|   [512, 512, 3] | 1021.60 |                     280.18 |                  340.40 |
|   [256, 256, 3] | 2234.31 |                     691.12 |                  769.29 |
|   [128, 128, 3] | 7713.83 |                     889.68 |                  968.23 |

### SmallestMaxSize

|          Shapes |  CPU FPS |    GPU with ToTensorV2 FPS | GPU without ToTensorV2 FPS |
| --------------- | -------- | -------------------------- | ----------------------- |
| [1024, 1024, 3] | 78736.70 |                     323.72 |                85163.53 |
|   [512, 512, 3] |  1496.99 |                    1457.26 |                 7132.08 |
|   [256, 256, 3] |  2374.33 |                    3456.97 |                 8324.36 |
|   [128, 128, 3] |  3025.39 |                    5002.12 |                 7752.97 |

### Transpose

|          Shapes |  CPU FPS |    GPU with ToTensorV2 FPS | GPU without ToTensorV2 FPS |
| --------------- | -------- | -------------------------- | ----------------------- |
| [1024, 1024, 3] | 81395.38 |                     328.75 |                51250.05 |
|   [512, 512, 3] | 65597.50 |                    1667.02 |                36934.70 |
|   [256, 256, 3] | 96456.26 |                    5191.00 |                48595.81 |
|   [128, 128, 3] | 94837.97 |                    9719.48 |                51034.91 |

### VerticalFlip

|          Shapes |  CPU FPS |    GPU with ToTensorV2 FPS | GPU without ToTensorV2 FPS |
| --------------- | -------- | -------------------------- | ----------------------- |
| [1024, 1024, 3] |  7246.30 |                     322.95 |                 4538.31 |
|   [512, 512, 3] | 18266.28 |                    1744.33 |                 9492.81 |
|   [256, 256, 3] | 45363.93 |                    4342.64 |                14249.43 |
|   [128, 128, 3] | 60185.16 |                    7006.58 |                14951.20 |