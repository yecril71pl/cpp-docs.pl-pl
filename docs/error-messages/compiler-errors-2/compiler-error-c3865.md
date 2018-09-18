---
title: Błąd kompilatora C3865 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3865
dev_langs:
- C++
helpviewer_keywords:
- C3865
ms.assetid: 9bc62bb0-4fb8-4856-a5cf-c7cb4029a596
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8fd5c83d922601ca4cdffe0f3772723b31e630b6
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46090844"
---
# <a name="compiler-error-c3865"></a>Błąd kompilatora C3865

"calling_convention": należy używać tylko w natywnych funkcjach składowych

Konwencja wywoływania był używany w funkcji, która została każda funkcja globalna lub funkcji składowej zarządzanej. Konwencja wywoływania należy używać tylko w funkcji natywnej (niezarządzane) elementu członkowskiego.

Aby uzyskać więcej informacji, zobacz [Konwencje wywoływania](../../cpp/calling-conventions.md).

Poniższy przykład spowoduje wygenerowanie C3865:

```
// C3865.cpp
// compile with: /clr
// processor: x86
void __thiscall Func(){}   // C3865

// OK
struct MyType {
   void __thiscall Func(){}
};
```