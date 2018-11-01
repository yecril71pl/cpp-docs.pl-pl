---
title: Kompilator ostrzeżenie (poziom 4) C4268
ms.date: 11/04/2016
f1_keywords:
- C4268
helpviewer_keywords:
- C4268
ms.assetid: d0511e80-904f-4ee1-b4d7-39b5c0bd8234
ms.openlocfilehash: e3cda7ed70963508d7663c6c12b2b98ac64db204
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50676502"
---
# <a name="compiler-warning-level-4-c4268"></a>Kompilator ostrzeżenie (poziom 4) C4268

'Identyfikator': "const" statyczne/globalne dane zainicjowano przy użyciu wygenerowanego przez kompilator domyślnego konstruktora, który wypełnił obiekt zerami

A **const** globalnych lub statycznych wystąpienia klasy nietrywialnymi jest inicjowany za pomocą generowanych przez kompilator domyślnego konstruktora.

## <a name="example"></a>Przykład

```
// C4268.cpp
// compile with: /c /LD /W4
class X {
public:
   int m_data;
};

const X x1;   // C4268
```

Ponieważ jest to wystąpienie klasy **const**, wartość `m_data` nie można jej zmienić.