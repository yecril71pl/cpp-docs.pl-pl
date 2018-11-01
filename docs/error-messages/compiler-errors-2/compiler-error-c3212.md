---
title: Błąd kompilatora C3212
ms.date: 11/04/2016
f1_keywords:
- C3212
helpviewer_keywords:
- C3212
ms.assetid: 9e271bb6-a51f-4b96-b26b-9f4ca28fca0a
ms.openlocfilehash: ac3e632894d269bb37860492c2bc63881fabe665
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50462351"
---
# <a name="compiler-error-c3212"></a>Błąd kompilatora C3212

"specjalizacja": jawna specjalizacja składowej szablonu musi być członkiem jawnej specjalizacji

Jawna specjalizacja został niewłaściwie sformatowany.

Poniższy przykład spowoduje wygenerowanie C3212:

```
// C3212.cpp
// compile with: /LD
template <class T>
struct S {
   template <class T1>
   struct S1;
};

template <class T>   // C3212
template <>
struct S<T>::S1<int> {};

/*
// try the following instead
template <>
template <>
struct S<int>::S1<int> {};
*/

/*
// or, the following
template <>
struct S<int> {
   template <class T1>
   struct S1;
};

template <>
struct S<int>::S1<int> {
};
*/
```