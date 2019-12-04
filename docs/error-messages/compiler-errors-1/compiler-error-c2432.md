---
title: Błąd kompilatora C2432
ms.date: 11/04/2016
f1_keywords:
- C2432
helpviewer_keywords:
- C2432
ms.assetid: 0e3326e8-cab1-45a5-b48d-61edd33793e8
ms.openlocfilehash: d4234626bc246d6da87be68b03d44562dd5990ff
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74744514"
---
# <a name="compiler-error-c2432"></a>Błąd kompilatora C2432

niedozwolone odwołanie do 16-bitowych danych w "identyfikatorze"

Rejestr 16-bitowy jest używany jako indeks lub rejestr podstawowy. Kompilator nie obsługuje przywołujących się do 16-bitowych danych. rejestry 16-bitowe nie mogą być używane jako indeksy ani rejestry bazowe podczas kompilowania kodu 32-bitowego.

Poniższy przykład generuje C2432:

```cpp
// C2432.cpp
// processor: x86
int main() {
   _asm mov eax, DWORD PTR [bx]   // C2432
}
```
