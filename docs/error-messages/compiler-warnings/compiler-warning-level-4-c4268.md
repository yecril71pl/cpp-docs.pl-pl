---
title: Kompilator ostrzeżenie (poziom 4) C4268 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4268
dev_langs:
- C++
helpviewer_keywords:
- C4268
ms.assetid: d0511e80-904f-4ee1-b4d7-39b5c0bd8234
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f91a8152ef690b9ded63b91b2b6e6f1da6dc2524
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46063713"
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