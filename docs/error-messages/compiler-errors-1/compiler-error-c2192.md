---
title: Błąd kompilatora C2192 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2192
dev_langs:
- C++
helpviewer_keywords:
- C2192
ms.assetid: a147197e-e72d-4620-939b-f9e08d7c7c12
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5d6cea2b4ce805c8f7d966ee9d2b3c27f8a901c8
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46023517"
---
# <a name="compiler-error-c2192"></a>Błąd kompilatora C2192

Parametr "number" deklaracji różni się

Funkcja języka C został zadeklarowany po raz drugi z inną listą parametrów. C nie obsługuje przeciążonych funkcji.

Poniższy przykład spowoduje wygenerowanie C2192:

```
// C2192.c
// compile with: /Za /c
void func( float, int );
void func( int, float );   // C2192, different parameter list
void func2( int, float );   // OK
```