---
title: Błąd kompilatora C3446
ms.date: 07/21/2017
f1_keywords:
- C3446
helpviewer_keywords:
- C3446
ms.assetid: 33064548-24e4-46f1-beb1-476e3c3b3fbf
ms.openlocfilehash: 0f9ebd274a90dffe00b0e8375cc374acf46e7a08
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447118"
---
# <a name="compiler-error-c3446"></a>Błąd kompilatora C3446

>"*Class*": domyślny inicjator składowej jest niedozwolony dla składowej klasy wartości

W programie Visual Studio 2015 i starszych kompilator dozwolony (ale ignorowany) domyślny inicjator elementu członkowskiego dla elementu członkowskiego klasy wartości. Domyślna Inicjalizacja klasy wartości zawsze zero — inicjuje członków; Konstruktor domyślny jest niedozwolony. W programie Visual Studio 2017 domyślne inicjatory elementów członkowskich zgłaszają błąd kompilatora, jak pokazano w tym przykładzie:

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

Aby poprawić błąd, Usuń inicjatora:

```cpp
// C3446b.cpp
value struct V
{
       int i;
       int j;
};
```

