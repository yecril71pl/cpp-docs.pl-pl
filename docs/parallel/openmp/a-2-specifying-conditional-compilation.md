---
title: A.2   Określanie kompilacji warunkowej
ms.date: 11/04/2016
ms.assetid: de4a21b9-f987-4738-9f13-c4795f6f2dff
ms.openlocfilehash: 92ae22ffac1b1a1c3fc45a9a7a883203ff6d251e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50491224"
---
# <a name="a2---specifying-conditional-compilation"></a>A.2   Określanie kompilacji warunkowej

Poniższe przykłady pokazują korzystanie z kompilacji warunkowej, użycie makra OpenMP `_OPENMP` ([sekcji 2.2](../../parallel/openmp/2-2-conditional-compilation.md) na stronie 8). Za pomocą kompilacji OpenMP `_OPENMP` makro staje się zdefiniowane.

```
# ifdef _OPENMP
    printf_s("Compiled by an OpenMP-compliant implementation.\n");
# endif
```

Zdefiniowane — operator preprocesora umożliwia więcej niż jednego makro testować w pojedynczej dyrektywy.

```
# if defined(_OPENMP) && defined(VERBOSE)
    printf_s("Compiled by an OpenMP-compliant implementation.\n");
# endif
```