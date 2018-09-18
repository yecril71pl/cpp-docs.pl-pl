---
title: Błąd kompilatora C2669 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2669
dev_langs:
- C++
helpviewer_keywords:
- C2669
ms.assetid: f9cb8111-bcdc-484b-a863-2c42e15a0496
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 04363816e69dd560acc0497128f13d92c9878005
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46050700"
---
# <a name="compiler-error-c2669"></a>Błąd kompilatora C2669

Funkcja składowa nie jest dozwolona w anonimowej Unii

[Związki anonimowe](../../cpp/unions.md#anonymous_unions) nie może mieć elementów członkowskich.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C2669:

```cpp
// C2669.cpp
struct X {
   union {
      int i;
      void f() {   // C2669, remove function
         i = 0;
      }
   };
};
```
