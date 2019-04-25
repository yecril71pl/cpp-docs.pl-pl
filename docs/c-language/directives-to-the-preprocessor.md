---
title: Dyrektywy preprocesora
ms.date: 11/04/2016
ms.assetid: adc6251e-cf6b-4508-bdbb-55f446c838d3
ms.openlocfilehash: 520d181c3a58ee2c626678a3afd9126f1ef183cc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62234143"
---
# <a name="directives-to-the-preprocessor"></a>Dyrektywy preprocesora

"Dyrektywy" powoduje, że preprocesora C, aby wykonywać konkretną akcję na podstawie tekstu programu przed kompilacją. [Dyrektywy preprocesora](../preprocessor/preprocessor-directives.md) opisano szczegółowo w *Preprocessor Reference*. W tym przykładzie użyto dyrektywy preprocesora `#define`:

```
#define MAX 100
```

Ta instrukcja informuje kompilator, aby zastąpić każde wystąpienie `MAX` przez `100` przed kompilacją. Dyrektywy preprocesora kompilatora C, to:

|#define|#endif|#ifdef|#line|
|--------------|-------------|-------------|------------|
|`#elif`|`#error`|**#ifndef**|**#pragma**|
|`#else`|`#if`|`#include`|`#undef`|

## <a name="see-also"></a>Zobacz także

[Pliki źródłowe i programy źródłowe](../c-language/source-files-and-source-programs.md)
