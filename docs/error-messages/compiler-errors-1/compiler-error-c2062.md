---
title: Błąd kompilatora C2062
ms.date: 11/04/2016
f1_keywords:
- C2062
helpviewer_keywords:
- C2062
ms.assetid: 6cc98353-2ddf-43ab-88a2-9cc91cdd6033
ms.openlocfilehash: dcfac9629a90b82744f87ec105c30301b2102cdf
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62408748"
---
# <a name="compiler-error-c2062"></a>Błąd kompilatora C2062

Typ 'typ' nieoczekiwany

Kompilator nie Oczekiwano nazwy typu.

Poniższy przykład spowoduje wygenerowanie C2062:

```
// C2062.cpp
// compile with: /c
struct A {  : int l; };   // C2062
struct B { private: int l; };   // OK
```

C2062 może również wystąpić, ze względu na sposób kompilator obsługuje typy niezdefiniowana w liście parametrów konstruktora. Gdy kompilator napotka niezdefiniowanego typu (czytelną?), zakłada się Konstruktor jest wyrażeniem, a następnie generuje C2062. Aby rozwiązać problem, używać tylko typów zdefiniowanych w liście parametrów konstruktora.