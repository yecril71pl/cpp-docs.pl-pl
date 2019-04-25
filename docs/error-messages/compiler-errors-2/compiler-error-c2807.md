---
title: Błąd kompilatora C2807
ms.date: 11/04/2016
f1_keywords:
- C2807
helpviewer_keywords:
- C2807
ms.assetid: bd7a207a-f379-4de6-8ee8-c7cab78b3480
ms.openlocfilehash: 5e3fd05b1c2473efbc1cd102056c73b2f221981d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62281920"
---
# <a name="compiler-error-c2807"></a>Błąd kompilatora C2807

drugi formalny parametr dla przyrostkowego "operator operator" musi być "int"

Drugi parametr przyrostkowego operatora ma nieprawidłowego typu.

Poniższy przykład spowoduje wygenerowanie C2807:

```
// C2807.cpp
// compile with: /c
class X {
public:
   X operator++ ( X );   // C2807 nonvoid parameter
   X operator++ ( int );   // OK, int parameter
};
```