---
title: Błąd kompilatora C2755
ms.date: 11/04/2016
f1_keywords:
- C2755
helpviewer_keywords:
- C2755
ms.assetid: 8ee4eeb6-4757-4efe-9100-38ff4a96f1de
ms.openlocfilehash: c2238058dc4b7df6bbe33e98d6ccde996f36b782
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62227975"
---
# <a name="compiler-error-c2755"></a>Błąd kompilatora C2755

"param": parametr typu innego niż stała parametryzująca składowej specjalizacji musi być prostym identyfikatorem

Parametr-type musi być prostym identyfikatorem, przez kompilator może rozpoznać w czasie kompilacji do jednego identyfikatora lub wartości stałej.

Poniższy przykład spowoduje wygenerowanie C2755:

```
// C2755.cpp
template<int I, int J>
struct A {};

template<int I>
struct A<I,I*5> {};   // C2755
// try the following line instead
// struct A<I,5> {};
```