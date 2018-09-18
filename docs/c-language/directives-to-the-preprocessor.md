---
title: Dyrektywy preprocesora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: adc6251e-cf6b-4508-bdbb-55f446c838d3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f1ddecf1e205cc9a6d7f09a27fbf243417540e49
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46033566"
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