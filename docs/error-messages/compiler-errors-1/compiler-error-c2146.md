---
title: Błąd kompilatora C2146
ms.date: 11/04/2016
f1_keywords:
- C2146
helpviewer_keywords:
- C2146
ms.assetid: 6bfb7de6-6723-4486-9350-c66ef88d7a64
ms.openlocfilehash: 3a0fd9c49a71f6f53d1a109378e3a6894bb68723
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50658071"
---
# <a name="compiler-error-c2146"></a>Błąd kompilatora C2146

Błąd składniowy: brakuje tokenu, przed identyfikatorem 'Identyfikator'

Kompilator oczekuje `token` i znaleźć `identifier` zamiast tego.  Możliwe przyczyny:

1. Błąd pisowni i wielkości liter.

1. Brak specyfikatora typu w deklaracji identyfikatora.

Ten błąd może być spowodowane błędem typograficzne. Błąd [C2065](../../error-messages/compiler-errors-1/compiler-error-c2065.md) poprzedza zazwyczaj ten błąd.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C2146.

```
// C2146.cpp
class CDeclaredClass {};

class CMyClass {
   CUndeclared m_myClass;   // C2146
   CDeclaredClass m_myClass2;   // OK
};

int main() {
   int x;
   int t x;   // C2146 : missing semicolon before 'x'
}
```

## <a name="example"></a>Przykład

Ten błąd może być też wygenerowany w wyniku pracy zgodności kompilatora, która została wykonana dla Visual Studio .NET 2003: Brak `typename` — słowo kluczowe.

Poniższy przykład kompiluje w Visual Studio .NET 2002, ale zakończy się niepowodzeniem w programie Visual Studio .NET 2003:

```
// C2146b.cpp
// compile with: /c
template <typename T>
struct X {
   struct Y {
      int i;
   };
   Y memFunc();
};

template <typename T>
X<T>::Y func() { }   // C2146

// OK
template <typename T>
typename X<T>::Y func() { }
```

## <a name="example"></a>Przykład

Zostanie również wyświetlony ten błąd w wyniku pracy zgodności kompilatora, która została wykonana dla Visual Studio .NET 2003: jawne specjalizacje nie są już znaleźć parametry szablonu z szablonu podstawowego.

Korzystanie z `T` z szablonu podstawowego nie jest dozwolona w jawnej specjalizacji. Aby kod był prawidłowy w wersjach programu Visual Studio .NET 2003 i Visual Studio .NET, Visual c++ należy zastąpić wszystkie wystąpienia parametru szablonu w specjalizacji jawnie specjalistyczną odmianą.

Poniższy przykład powoduje kompilację w programie Visual Studio .NET, ale zakończy się niepowodzeniem w programie Visual Studio .NET 2003:

```
// C2146_c.cpp
// compile with: /c
template <class T>
struct S;

template <>
struct S<int> {
   T m_t;   // C2146
   int m_t2;   // OK
};
```