---
title: Błąd kompilatora C2785 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2785
dev_langs:
- C++
helpviewer_keywords:
- C2785
ms.assetid: d8d13360-0d00-4815-8475-b49c7f0dc0f3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cfae8a58d9c42c9ddc3ef7779fc86f7157ba41b0
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46080860"
---
# <a name="compiler-error-c2785"></a>Błąd kompilatora C2785

"declaration1" i "declaration2" mają różne typy zwracane

Zwracany typ specjalizacja szablonu funkcji różni się od zwracany typ szablonu podstawowej funkcji.

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

1. Sprawdź wszystkie specjalizacje szablonu funkcji w celu zachowania spójności.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C2785:

```
// C2785.cpp
// compile with: /c
template<class T> void f(T);

template<> int f(int); // C2785
template<> void f(int); // OK
```