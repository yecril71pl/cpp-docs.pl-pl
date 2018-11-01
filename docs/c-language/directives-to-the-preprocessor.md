---
title: Dyrektywy preprocesora
ms.date: 11/04/2016
ms.assetid: adc6251e-cf6b-4508-bdbb-55f446c838d3
ms.openlocfilehash: 0abc21f38f5776acd9167f0526160dc5e1bb8cbb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50450070"
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

## <a name="see-also"></a>Zobacz też

[Pliki źródłowe i programy źródłowe](../c-language/source-files-and-source-programs.md)