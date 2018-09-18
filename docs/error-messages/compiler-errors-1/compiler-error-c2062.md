---
title: Błąd kompilatora C2062 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2062
dev_langs:
- C++
helpviewer_keywords:
- C2062
ms.assetid: 6cc98353-2ddf-43ab-88a2-9cc91cdd6033
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bbda0894b25e09681207d6447bb40727d490fc02
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46072254"
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