---
title: Błąd kompilatora C3536 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3536
dev_langs:
- C++
helpviewer_keywords:
- C3536
ms.assetid: 8d866075-866b-49eb-9979-ee27b308f7e3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7585a75ebe9733c228756e92d8e5ae57699aca27
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46088582"
---
# <a name="compiler-error-c3536"></a>Błąd kompilatora C3536

'symbol': nie można użyć, zanim zostanie zainicjowany

Nie można użyć symbol koła wskazane, zanim zostanie zainicjowany. W praktyce oznacza to, że zmienna nie może służyć do zainicjowania.

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

1. Nie Inicjuj zmienną z samym sobą.

## <a name="example"></a>Przykład

Poniższy przykład daje C3536, ponieważ każda zmienna jest inicjowana z samym sobą.

```
// C3536.cpp
// Compile with /Zc:auto
int main()
{
   auto a = a;     //C3536
   auto b = &b;    //C3536
   auto c = c + 1; //C3536
   auto* d = &d;   //C3536
   auto& e = e;    //C3536
   return 0;
};
```

## <a name="see-also"></a>Zobacz też

[Auto, słowo kluczowe](../../cpp/auto-keyword.md)