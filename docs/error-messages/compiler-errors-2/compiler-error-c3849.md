---
title: Błąd kompilatora C3849 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3849
dev_langs:
- C++
helpviewer_keywords:
- C3849
ms.assetid: 5347140e-1a81-4841-98c0-b63d98264b64
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 08f89deb3bd83162dd7cf5dc80335e5274efa1c7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46077506"
---
# <a name="compiler-error-c3849"></a>Błąd kompilatora C3849

Wywołanie w stylu funkcji na wyrażeniu typu "type" spowoduje utratę kwalifikatorów const i/lub volatile dla wszystkich liczba dostępnych przeciążeń operatora

Zmienna przy użyciu określonego typu const-volatile może wywołać tylko elementu członkowskiego funkcje zdefiniowane przy użyciu tej samej lub większej kwalifikacji const-volatile.

Aby naprawić ten błąd, zapewnia funkcja właściwego członka. Nie można wykonać konwersji na typu const ani volatile obiektów kwalifikowaną, jeśli konwersja powoduje utratę kwalifikacji. Możesz uzyskać kwalifikatorów, ale nie utratę kwalifikatorów, podczas konwersji.

Poniższe przykłady generują C3849:

```
// C3849.cpp
void glbFunc3(int i, char c)
{
   i;
}
typedef void (* pFunc3)(int, char);

void glbFunc2(int i)
{
   i;
}

typedef void (* pFunc2)(int);

void glbFunc1()
{
}
typedef void (* pFunc1)();

struct S4
{
   operator ()(int i)
   {
      i;
   }

   operator pFunc1() const
   {
      return &glbFunc1;
   }

   operator pFunc2() volatile
   {
      return &glbFunc2;
   }

   operator pFunc3()
   {
      return &glbFunc3;
   }

   // operator pFunc1() const volatile
   // {
   //    return &glbFunc1;
   // }
};

int main()
{
   // Cannot call any of the 4 overloads of "operator ()(.....)" and
   // "operator pFunc()" because none is declared as "const volatile"
   const volatile S4 s4;  // can only call cv member functions of S4
   s4();   // C3849 to resolve, uncomment member function
}
```