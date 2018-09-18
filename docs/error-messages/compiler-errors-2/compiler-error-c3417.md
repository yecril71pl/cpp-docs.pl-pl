---
title: Błąd kompilatora C3417 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3417
dev_langs:
- C++
helpviewer_keywords:
- C3417
ms.assetid: 3e7869ea-8948-42fb-ba30-6ccafe499c35
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8b21636c3500625f262355750d32aa0fa3faeb5d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46073853"
---
# <a name="compiler-error-c3417"></a>Błąd kompilatora C3417

"członek": typy wartości nie może zawierać funkcji specjalnych elementów członkowskich zdefiniowanych przez użytkownika

Typy wartości nie może zawierać funkcji, takich jak konstruktora wystąpienia domyślnego, destruktor lub konstruktorem kopiującym.

Poniższy przykład spowoduje wygenerowanie C3517:

```
// C3417.cpp
// compile with: /clr /c
value class VC {
   VC(){}   // C3417

   // OK
   static VC(){}
   VC(int i){}
};
```