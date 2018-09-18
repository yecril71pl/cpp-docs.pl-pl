---
title: Błąd kompilatora C2461 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2461
dev_langs:
- C++
helpviewer_keywords:
- C2461
ms.assetid: e64ba651-f441-4fdb-b5cb-4209bbbe4db4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 39d58b315fdd7e3c4e1899041cebf8400813ed40
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46029302"
---
# <a name="compiler-error-c2461"></a>Błąd kompilatora C2461

> "*klasy*": składni konstruktora brakuje parametrów formalnych

Konstruktor dla klasy nie określono żadnych parametrów formalnych. Deklaracja konstruktora, należy określić formalnej listy parametrów. Lista może być pusta.

Aby rozwiązać ten problem, Dodaj parę nawiasów po zadeklarowaniu *klasy*:: **klasy*.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak naprawić C2461:

```cpp
// C2461.cpp
// compile with: /c
class C {
   C::C;     // C2461
   C::C();   // OK
};
```