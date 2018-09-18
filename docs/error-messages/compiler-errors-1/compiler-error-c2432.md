---
title: Błąd kompilatora C2432 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2432
dev_langs:
- C++
helpviewer_keywords:
- C2432
ms.assetid: 0e3326e8-cab1-45a5-b48d-61edd33793e8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9ca8c2c62415b6ec3c29c820a23677a87a2695c5
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46055913"
---
# <a name="compiler-error-c2432"></a>Błąd kompilatora C2432

niedozwolone odwołanie do 16-bitowych danych w 'Identyfikator'

Rejestr 16-bitowy jest używany jako indeksu lub klucza rejestru podstawowej. Kompilator nie obsługuje odwołujące się do 16-bitowych danych. 16-bitowych rejestrów nie można użyć jako indeks lub base rejestrów, podczas kompilowania kodu 32-bitowych.

Poniższy przykład spowoduje wygenerowanie C2432:

```
// C2432.cpp
// processor: x86
int main() {
   _asm mov eax, DWORD PTR [bx]   // C2432
}
```