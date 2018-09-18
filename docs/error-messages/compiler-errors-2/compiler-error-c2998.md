---
title: Błąd kompilatora C2998 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2998
dev_langs:
- C++
helpviewer_keywords:
- C2998
ms.assetid: 8193d491-b5d9-4477-acb1-cf166889c070
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 181db50f9b2598379d1b9d56720551f1b18cbf18
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46118430"
---
# <a name="compiler-error-c2998"></a>Błąd kompilatora C2998

'Identyfikator': nie może być definicją szablonu

Kompilator nie może przetworzyć składnią używaną w definicji szablonu.

Poniższy przykład spowoduje wygenerowanie C2998:

```
// C2998.cpp
// compile with: /c
template <class T> int x = 1018; // C2998
```