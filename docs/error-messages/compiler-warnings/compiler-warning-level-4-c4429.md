---
title: Ostrzeżenie kompilatora (poziom 4) C4429
ms.date: 11/04/2016
f1_keywords:
- C4429
helpviewer_keywords:
- C4429
ms.assetid: a3e4cf1f-a869-4e47-834a-850c21eb5297
ms.openlocfilehash: 6702db4af5c31d21610e02b1a4ec75af27ad10f2
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2019
ms.locfileid: "74990824"
---
# <a name="compiler-warning-level-4-c4429"></a>Ostrzeżenie kompilatora (poziom 4) C4429

możliwa niekompletna lub nieprawidłowo sformułowana nazwa znaku uniwersalnego

Kompilator wykrył sekwencję znaków, która może być błędnie sformatowaną nazwą znaku uniwersalnego. Nazwa uniwersalnego znaku jest `\u` po którym następują cztery cyfry szesnastkowe lub `\U` po nich osiem cyfr szesnastkowych.

Poniższy przykład generuje C4429:

```cpp
// C4429.cpp
// compile with: /W4 /WX
int \ug0e4 = 0;   // C4429
// Try the following line instead:
// int \u00e4 = 0;   // OK, a well-formed universal character name.
```
