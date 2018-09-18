---
title: Kompilator ostrzeżenie (poziom 1) C4083 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4083
dev_langs:
- C++
helpviewer_keywords:
- C4083
ms.assetid: e7d3344e-5645-4d56-8460-d1acc9145ada
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 64e81b6a68a9584e4fb30829e15da6472212ce05
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46046371"
---
# <a name="compiler-warning-level-1-c4083"></a>Kompilator ostrzeżenie (poziom 1) C4083

Oczekiwano 'token'; Znaleziono identyfikator 'Identyfikator'

Identyfikator odbywa się w niewłaściwym miejscu w **#pragma** instrukcji.

## <a name="example"></a>Przykład

```
// C4083.cpp
// compile with: /W1 /LD
#pragma warning disable:4083    // C4083
#pragma warning(disable:4083)   //correct
```

Sprawdź składnię [#pragma](../../preprocessor/pragma-directives-and-the-pragma-keyword.md) dyrektywy.