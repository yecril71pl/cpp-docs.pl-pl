---
title: C3445 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 04/10/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3445
dev_langs:
- C++
helpviewer_keywords:
- C3445
ms.assetid: 0d272bfc-136b-4025-a9ba-5e4eea5f8215
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4c37f04b907183b883772fd144ae0179683f088f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3445"></a>C3445 błąd kompilatora

> kopiowania listy Inicjalizacja "*typu*" nie można użyć jawny Konstruktor

ISO standardzie C ++ 17 kompilator jest wymagane uwzględnienie jawny Konstruktor Rozpoznanie przeciążenia w Inicjalizacja listy kopii, ale musi Zgłoś błąd, jeśli faktycznie jest wybierany tego przeciążenia.

Począwszy od programu Visual Studio 2017 kompilator znajduje błędy dotyczące tworzenia obiektów za pomocą listy inicjalizatora, które nie zostały odnalezione w programie Visual Studio 2015. Te błędy może prowadzić do awarii lub niezdefiniowane zachowanie w czasie wykonywania.

## <a name="example"></a>Przykład

Poniższy przykład generuje C3445.

```cpp
// C3445.cpp
struct A
{
    explicit A(int) {}
    A(double) {}
};

int main()
{
    A a1 = { 1 };     // error C3445: copy-list-initialization of
                      //     'A' cannot use an explicit constructor
}
```

Aby rozwiązać problem, należy użyć bezpośredniego inicjowania:

```cpp
// C3445b.cpp
struct A
{
    explicit A(int) {}
    A(double) {}
};

int main()
{
    A a1{ 1 };
}
```
