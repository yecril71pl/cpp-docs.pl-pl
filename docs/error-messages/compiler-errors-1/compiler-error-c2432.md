---
title: Błąd kompilatora C2432
ms.date: 11/04/2016
f1_keywords:
- C2432
helpviewer_keywords:
- C2432
ms.assetid: 0e3326e8-cab1-45a5-b48d-61edd33793e8
ms.openlocfilehash: e2983d966a6290ce19713c63feb502c8ffc74bf1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62166844"
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