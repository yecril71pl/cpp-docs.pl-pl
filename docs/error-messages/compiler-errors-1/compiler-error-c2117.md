---
title: Błąd kompilatora C2117 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2117
dev_langs:
- C++
helpviewer_keywords:
- C2117
ms.assetid: b947379d-5861-42fc-ac26-170318579cbd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e5579a6f05e1de768aebd2e68b64d0b861688607
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46030996"
---
# <a name="compiler-error-c2117"></a>Błąd kompilatora C2117

'Identyfikator': przepełnienie granic tablicy

Tablica ma zbyt wiele inicjatorów:

- Inicjatory i elementy tablicy nie są zgodne rozmiaru i liczby.

- Nie miejsca dla terminator o wartości null w ciągu.

Poniższy przykład spowoduje wygenerowanie C2117:

```
// C2117.cpp
int main() {
   char abc[4] = "abcd";   // C2117
   char def[4] = "abd";   // OK
}
```