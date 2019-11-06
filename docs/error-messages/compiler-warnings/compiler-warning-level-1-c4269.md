---
title: Ostrzeżenie kompilatora (poziom 1) C4269
ms.date: 11/04/2016
f1_keywords:
- C4269
helpviewer_keywords:
- C4269
ms.assetid: 96c97bbc-068a-4b65-8cd8-4ed5dca04c15
ms.openlocfilehash: 84a0d4c541f67742d68c7f08e0dda52ccd350d04
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626710"
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