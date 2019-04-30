---
title: Błąd kompilatora C2912
ms.date: 11/04/2016
f1_keywords:
- C2912
helpviewer_keywords:
- C2912
ms.assetid: bd55cecd-ab1a-4636-ab8a-a00393fe7b3d
ms.openlocfilehash: b7f87ae2df5350fcfb2b7a662f517d8d7bd51ef8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62408397"
---
# <a name="compiler-error-c2912"></a>Błąd kompilatora C2912

jawna specjalizacja "deklaracją" nie jest specjalizacją szablonu funkcji

Nie można specjalizować funkcji inne niż szablonu.

Poniższy przykład spowoduje wygenerowanie C2912:

```
// C2912.cpp
// compile with: /c
void f(char);
template<> void f(char);   // C2912
template<class T> void f(T);   // OK
```

Ten błąd będzie też można wygenerować w wyniku pracy zgodności kompilatora, która została wykonana w Visual Studio .NET 2003: dla każdej jawna specjalizacja, musisz wybrać parametry jawna specjalizacja taki sposób, że są zgodne z parametrami podstawową szablon.

```
// C2912b.cpp
class CF {
public:
   template <class A> CF(const A& a) {}   // primary template

   // attempted explicit specialization
   template <> CF(const char* p) {}   // C2912

   // try the following line instead
   // template <> CF(const char& p) {}
};
```