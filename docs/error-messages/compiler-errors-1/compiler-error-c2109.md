---
title: Błąd kompilatora C2109 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2109
dev_langs:
- C++
helpviewer_keywords:
- C2109
ms.assetid: 2d1ac79d-a985-4904-a38b-b270578d664d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 551c391c67e54c00a26fe6c11fb062adcb9c2f30
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46100796"
---
# <a name="compiler-error-c2109"></a>Błąd kompilatora C2109

Indeks dolny wymaga tablicy lub wskaźnika typu

Indeks dolny została użyta w zmiennej, która nie jest tablicą.

Poniższy przykład spowoduje wygenerowanie C2109:

```
// C2109.cpp
int main() {
   int a, b[10] = {0};
   a[0] = 1;   // C2109
   b[0] = 1;   // OK
}
```