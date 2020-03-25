---
title: Ostrzeżenie kompilatora (poziom 1) C4269
ms.date: 11/04/2016
f1_keywords:
- C4269
helpviewer_keywords:
- C4269
ms.assetid: 96c97bbc-068a-4b65-8cd8-4ed5dca04c15
ms.openlocfilehash: e2e1781bf4c1b9ac0ee29d0b5900daa6cfe94b45
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80199774"
---
# <a name="compiler-warning-level-1-c4269"></a>Ostrzeżenie kompilatora (poziom 1) C4269

"Identyfikator": "const" automatyczne dane zainicjowane przy użyciu domyślnego konstruktora wygenerowanego przez kompilator produkuje niezawodne wyniki

**Stałe** automatyczne wystąpienie klasy nieuproszczonej jest inicjowane za pomocą domyślnego konstruktora wygenerowanego przez kompilator.

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

Ponieważ to wystąpienie klasy jest generowane na stosie, początkowa wartość `m_data` może być dowolna. Ponadto, ponieważ jest to wystąpienie **stałe** , wartość `m_data` nigdy nie może zostać zmieniona.
