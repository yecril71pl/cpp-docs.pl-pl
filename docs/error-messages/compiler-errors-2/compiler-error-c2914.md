---
title: Błąd kompilatora C2914
ms.date: 11/04/2016
f1_keywords:
- C2914
helpviewer_keywords:
- C2914
ms.assetid: fc6a0592-f53e-4f5a-88cb-780bbed4acf2
ms.openlocfilehash: 2500736f799032aea71173931139404b4406a16a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50659597"
---
# <a name="compiler-error-c2914"></a>Błąd kompilatora C2914

'Identyfikator': nie można wywnioskować argumentów typu jako argumentu funkcji jest niejednoznaczny

Kompilator nie może określić, które przeciążone funkcje, aby użyć argumentu generyczny lub szablonu.

Poniższy przykład spowoduje wygenerowanie C2914:

```
// C2914.cpp
// compile with: /c
void f(int);
void f(double);
template<class T> void g(void (*) (T));
void h() { g(f); }   // C2914
// try the following line instead
// void h() { g<int>(f); }
```

C2914 może również wystąpić, gdy za pomocą typów ogólnych.  Poniższy przykład spowoduje wygenerowanie C2914:

```
// C2914b.cpp
// compile with: /clr /c
void f(int);
void f(double);

template<class T>
void gf(void (*) (T));

void h() { gf(f);}   // C2914
// try the following line instead
void h() { gf<int>(f); }
```