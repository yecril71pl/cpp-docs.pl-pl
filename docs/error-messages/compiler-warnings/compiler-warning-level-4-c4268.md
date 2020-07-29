---
title: Ostrzeżenie kompilatora (poziom 4) C4268
ms.date: 11/04/2016
f1_keywords:
- C4268
helpviewer_keywords:
- C4268
ms.assetid: d0511e80-904f-4ee1-b4d7-39b5c0bd8234
ms.openlocfilehash: 1db8f67591560c130bc25c40c63232f54b3b7884
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219914"
---
# <a name="compiler-warning-level-4-c4268"></a>Ostrzeżenie kompilatora (poziom 4) C4268

"Identyfikator": "const" dane statyczne/globalne zainicjowane przy użyciu konstruktora domyślnego wygenerowanego przez kompilator wypełniają obiekt zerami

**`const`** Globalne lub statyczne wystąpienie klasy nieuproszczonej jest inicjowane za pomocą domyślnego konstruktora wygenerowanego przez kompilator.

## <a name="example"></a>Przykład

```cpp
// C4268.cpp
// compile with: /c /LD /W4
class X {
public:
   int m_data;
};

const X x1;   // C4268
```

Ponieważ to wystąpienie klasy ma **`const`** wartość, `m_data` nie można zmienić wartości.
