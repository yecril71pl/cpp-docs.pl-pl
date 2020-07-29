---
title: Ostrzeżenie kompilatora (poziom 1) C4269
ms.date: 11/04/2016
f1_keywords:
- C4269
helpviewer_keywords:
- C4269
ms.assetid: 96c97bbc-068a-4b65-8cd8-4ed5dca04c15
ms.openlocfilehash: 1b63d1af49a53b7b15cdbae912d79a1b4f0cf787
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230717"
---
# <a name="compiler-warning-level-1-c4269"></a>Ostrzeżenie kompilatora (poziom 1) C4269

"Identyfikator": "const" automatyczne dane zainicjowane przy użyciu domyślnego konstruktora wygenerowanego przez kompilator produkuje niezawodne wyniki

**`const`** Automatyczne wystąpienie klasy nieuproszczonej jest inicjowane za pomocą domyślnego konstruktora wygenerowanego przez kompilator.

## <a name="example"></a>Przykład

```cpp
// C4269.cpp
// compile with: /c /LD /W1
class X {
public:
   int m_data;
};

void g() {
   const X x1;   // C4269
};
```

Ponieważ to wystąpienie klasy jest generowane na stosie, początkowa wartość `m_data` może być dowolna. Ponadto, ponieważ jest to **`const`** wystąpienie, wartość `m_data` nie może być nigdy zmieniana.
