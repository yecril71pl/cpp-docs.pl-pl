---
title: Kompilator ostrzeżenie (poziom 3) C4334 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4334
dev_langs:
- C++
helpviewer_keywords:
- C4334
ms.assetid: d845857f-bc95-4faf-a079-626a0cf935ba
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4b7bb16ea38b2c2112c12c561398341a7d1adbfc
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46044018"
---
# <a name="compiler-warning-level-3-c4334"></a>Kompilator ostrzeżenie (poziom 3) C4334

'operator': wynik 32-bitowe przesunięcia niejawnie skonwertowano do 64 bitów (była 64-bitowe przesunięcie przeznaczone?)

Wynik 32-bitowe przesunięcia niejawnie został przekonwertowany na 64-bitowej i kompilatora podejrzewa, że 64-bitowe przesunięcie było zamierzone.  Aby rozwiązać to ostrzeżenie, użyj 64-bitowe przesunięcie albo jawnie rzutowane wynik przesunięcia do 64-bitowej.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C4334.

```
// C4334.cpp
// compile with: /W3 /c
void SetBit(unsigned __int64 *p, int i) {
   *p |= (1 << i);   // C4334
   *p |= (1i64 << i);   // OK
}
```