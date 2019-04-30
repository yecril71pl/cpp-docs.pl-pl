---
title: Błąd kompilatora C2287
ms.date: 11/04/2016
f1_keywords:
- C2287
helpviewer_keywords:
- C2287
ms.assetid: 64556299-4e1f-4437-88b7-2464fc0b95bb
ms.openlocfilehash: f5493220c4380d1fd67b38995414f48a2ef72a41
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62385826"
---
# <a name="compiler-error-c2287"></a>Błąd kompilatora C2287

"class": reprezentacja dziedziczenia: "representation1" jest mniej ogólny niż wymagany representation2

Klasa jest zadeklarowana za pomocą reprezentację prostsze, niż jest to wymagane.

Poniższy przykład spowoduje wygenerowanie C2287:

```
// C2287.cpp
// compile with: /vmg /c
class __single_inheritance X;
class __single_inheritance Y;

struct A { };
struct B { };
struct X : A, B { };  // C2287  X uses multiple inheritance
struct Y : A { };  // OK
```