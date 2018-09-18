---
title: Kompilator ostrzeżenie (poziom 1) C4052 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4052
dev_langs:
- C++
helpviewer_keywords:
- C4052
ms.assetid: f9955421-16ab-46e5-8f9d-bf1639a519ef
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 67e63f694a190a3d7c694fa99ff0433870a1b9c5
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46103408"
---
# <a name="compiler-warning-level-1-c4052"></a>Kompilator ostrzeżenie (poziom 1) C4052

deklaracje funkcji, inny, jeden z nich zawiera zmienne argumenty

Jedna deklaracja funkcji nie zawiera zmiennych argumentów. Jest on ignorowany.

Poniższy przykład spowoduje wygenerowanie C4052:

```
// C4052.c
// compile with: /W4 /c
int f();
int f(int i, ...);   // C4052
```