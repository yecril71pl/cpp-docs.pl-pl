---
title: Błąd kompilatora C2040
ms.date: 11/04/2016
f1_keywords:
- C2040
helpviewer_keywords:
- C2040
ms.assetid: 74ca3592-1469-4965-ab34-a4815e2fbefe
ms.openlocfilehash: b45ec25f1ed516ae73b242fdcc7c66f68c92f724
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62387113"
---
# <a name="compiler-error-c2040"></a>Błąd kompilatora C2040

'operator': "identifier1" różni się w poziomach pośredników od "identifier2"

Wyrażenie obejmujące operandy określonego ma niezgodne argumentami o typach lub niejawnie przekonwertować typy argumentów operacji. Jeśli oba operandy są arytmetycznego lub jedne i drugie są nonarithmetic (na przykład tablicy lub wskaźnika), są one używane bez zmian. Jeśli jeden z operandów jest arytmetyczne, a druga nie jest, arytmetyczny operand jest konwertowany na typ operandu nonarithmetic.

Ten przykład generuje C2040 i pokazuje, jak go naprawić.

```
// C2040.cpp
// Compile by using: cl /c /W3 C2040.cpp
bool test() {
   char c = '3';
   return c == "3"; // C2446, C2040
   // return c == '3'; // OK
}
```