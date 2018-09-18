---
title: Błąd kompilatora C2755 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2755
dev_langs:
- C++
helpviewer_keywords:
- C2755
ms.assetid: 8ee4eeb6-4757-4efe-9100-38ff4a96f1de
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 56ecf997df2aeb1a41b5021d61b24073e871b55f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46064921"
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