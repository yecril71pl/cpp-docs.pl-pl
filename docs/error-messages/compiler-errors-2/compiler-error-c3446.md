---
title: Błąd kompilatora C3446 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 07/21/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3446
dev_langs:
- C++
helpviewer_keywords:
- C3445
ms.assetid: 33064548-24e4-46f1-beb1-476e3c3b3fbf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a88bb77489d2596c271842e7becb0214d1af2821
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46018870"
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

