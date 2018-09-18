---
title: Błąd kompilatora C2423 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2423
dev_langs:
- C++
helpviewer_keywords:
- C2423
ms.assetid: 8797fb8b-b58b-4add-b6e6-2a9a3cd9084d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5e7a974a83935dbbcc9cd78bcc9280c9f0fbc2a4
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46029315"
---
# <a name="compiler-error-c2423"></a>Błąd kompilatora C2423

"numer": niedozwolona Skala

Wbudowany kod asemblera używa wielu innych niż 1, 2, 4 lub 8 skalowanie do rejestru.

Poniższy przykład spowoduje wygenerowanie C2423:

```
// C2423.cpp
// processor: x86
int main() {
   _asm {
      lea EAX, [EAX*3]   // C2423
      lea EAX, [EAX+EAX*2]   // OK
   }
}
```