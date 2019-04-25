---
title: Kompilator ostrzeżenie (poziom 1) C4269
ms.date: 11/04/2016
f1_keywords:
- C4269
helpviewer_keywords:
- C4269
ms.assetid: 96c97bbc-068a-4b65-8cd8-4ed5dca04c15
ms.openlocfilehash: 9a7f42b2dd65644d3f2abec58236a0b93cc6f635
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62207236"
---
# <a name="compiler-warning-level-1-c4269"></a>Kompilator ostrzeżenie (poziom 1) C4269

'Identyfikator': "const" automatyczne dane zainicjowano przy użyciu wygenerowanego przez kompilator domyślnego konstruktora, który zwrócił niepewne wyniki

A **const** automatyczne wystąpienia klasy nietrywialnymi jest inicjowany za pomocą generowanych przez kompilator domyślnego konstruktora.

## <a name="example"></a>Przykład

```
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

Ponieważ to wystąpienie klasy jest generowany na stosie, początkowa wartość `m_data` może być dowolna. Ponadto, ponieważ jest **const** wystąpienia wartości `m_data` nigdy nie można zmienić.