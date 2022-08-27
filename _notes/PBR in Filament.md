#PBR #3D
[[PBR]] = Physically-based Rendering 的簡稱。

相較傳統的實時渲染模型，PBR 可以更準確的表現物體表面的材質以前跟光線互動的行為。

Source: https://google.github.io/filament/Filament.html#overview

本文主要來自於 Filament PBR 說明

## Filament Standard Model

用數學來描述標準模型，叫做 BSDF (Bidirectional Scattering Distribution Function)

BSDF 由兩個部分組成
1. BRDF (Bidirectional Reflection Distribution Function)
2. BTDF (Bidirectional Transmittance Distribution Function)

實務上，通常會忽略，或者極簡化 BTDF，然後專注於處理 BRDF。因為這是生活中大多數平面的材質。


BRDF ![[diagram_fr_fd.png]]

fd = 散射部分 fr 反射部分

所以 BRDF 的數學公式可以寫成如下

f(v, l) = fd(v, l) + fr(v, l)

v: 觀測方向的單位向量
l: 入射光線的單位向量

這個公式概略描述了單一入射光線的情況。真實情況，需要積分整個半球的入射光線 (對 l 積分)


## microfacet BRDF

microfacet BRDF 微平面 BRDF
good practical plausible 可行的 BRDF 模型

在微觀視野，平面都是由非常微小的凹凸不平的平面組成的。

D term: