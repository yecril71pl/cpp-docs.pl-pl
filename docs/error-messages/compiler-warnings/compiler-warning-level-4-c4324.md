---
title: Kompilator ostrzeżenie (poziom 4) C4324 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4324
dev_langs:
- C++
helpviewer_keywords:
- C4324
ms.assetid: 420fa929-d9c0-40b4-8808-2d8ad3ca8090
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2499aa7c674e3bd1bece14c39b09f9863d6bb783
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46064792"
---
# <a name="compiler-warning-level-4-c4324"></a>Kompilator ostrzeżenie (poziom 4) C4324

"struct_name": struktura została wzmocniona ze względu na __declspec(align())

Dopełnienie został dodany na końcu struktury, ponieważ określono [__declspec(align)](../../cpp/align-cpp.md) wartości.

Na przykład poniższy kod generuje C4324:

```
// C4324.cpp
// compile with: /W4
struct __declspec(align(32)) A
{
   char a;
};   // C4324

int main()
{
}
```