---
title: Kompilator ostrzeżenie (poziom 1) C4269 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4269
dev_langs:
- C++
helpviewer_keywords:
- C4269
ms.assetid: 96c97bbc-068a-4b65-8cd8-4ed5dca04c15
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6dc986c98028530b8a5d4d25047305fd1a8effef
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46027283"
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