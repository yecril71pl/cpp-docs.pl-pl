---
title: Błąd kompilatora C3446
ms.date: 07/21/2017
f1_keywords:
- C3446
helpviewer_keywords:
- C3445
ms.assetid: 33064548-24e4-46f1-beb1-476e3c3b3fbf
ms.openlocfilehash: 8145e0cdd97022ebdcc1a7ce38c8860a005945b0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50631123"
---
# <a name="compiler-error-c3446"></a>Błąd kompilatora C3446

>"*klasy*": domyślny inicjator składowej nie jest dozwolona dla składowej klasy wartości

W programie Visual Studio 2015 lub starszego kompilatora dozwolone (ale ignorowane) domyślny inicjator składowej dla składowej klasy wartości. Domyślna Inicjalizacja klasy wartości zawsze zero inicjuje członków; domyślny konstruktor nie jest dozwolone. W programie Visual Studio 2017 domyślny element członkowski inicjatory podnieść błąd kompilatora, jak pokazano w poniższym przykładzie:

## <a name="example"></a>Przykład

Poniższy przykład generuje C3446 w programie Visual Studio 2017 i nowszych:

```cpp
// C3446.cpp
value struct V
{
       int i = 0; // error C3446: 'V::i': a default member initializer
                  // is not allowed for a member of a value class
       int j {0}; // C3446
};
```

Aby poprawić ten błąd, Usuń inicjatora:

```cpp
// C3446b.cpp
value struct V
{
       int i;
       int j;
};
```

