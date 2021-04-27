<!--
 * @Author: tangdaoyong
 * @Date: 2021-04-27 12:04:00
 * @LastEditors: tangdaoyong
 * @LastEditTime: 2021-04-27 12:06:43
 * @Description: filter
-->
# filter

filter有许多强大的功能，比如修改图片亮度、对比度、饱和度，进行高斯模糊等功能
filter: none | blur() | brightness() | contrast() | drop-shadow() | grayscale() | hue-rotate() | invert() | opacity() | saturate() | sepia() | url();

## 高斯模糊
filter: blur(px) 单位只能是像素. 设置几像素 模糊效果就已经很明显了

## 亮度
filter： brightness(%).  0%(全黑)-100%(原图亮度)、 >100%：高亮

## 对比度
filter: contrast(%).  0%(全黑)-100%(原图)、 >100%：更高的对比度

## 饱和度
filter: saturate(%).   0%(完全不饱和，黑白图片)-100%(原图)、 >100%：更高的饱和度

## 反转
filter: invert(%).  0%(原图)-50%(灰色度)、50%-100%：类似胶卷底片的效果。>100%和100%的效果一样

## 褐色
filter: sepia(%).   0%(原图)-100%(褐色图片) . >100%和100%的效果一样

## 色相旋转
filter: hue-rotate(deg).   0deg - 360deg。大约是以90多分为四个区间.  以360deg为循环，即：0=360=720的效果