---
title: Błąd kompilatora C2040 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2040
dev_langs:
- C++
helpviewer_keywords:
- C2040
ms.assetid: 74ca3592-1469-4965-ab34-a4815e2fbefe
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ccfbacff97550e20c0dd0202e0737585ffd39d6d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46016471"
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