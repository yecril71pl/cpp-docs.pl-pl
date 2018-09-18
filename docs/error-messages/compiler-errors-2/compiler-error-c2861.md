---
title: Błąd kompilatora C2861 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2861
dev_langs:
- C++
helpviewer_keywords:
- C2861
ms.assetid: 012bb44d-6c9b-4def-b54e-b19f1f8ddd1b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 94210350e0483b46eb86579b837501a5291bda4d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46037258"
---
# <a name="compiler-error-c2861"></a>Błąd kompilatora C2861

"Nazwa funkcji": funkcja składowa interfejsu nie może być zdefiniowana

Kompilator napotkał interface — słowo kluczowe lub wywnioskowany; dotyczy to struktura jako interfejs, ale następnie znaleziono członka definicji funkcji.  Interfejs nie może zawierać definicję dla funkcji członkowskiej.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C2861:

```
// C2861.cpp
// compile with: /c
#include <objbase.h>   // required for IUnknown definition
[ object, uuid("00000000-0000-0000-0000-000000000001") ]
__interface IMyInterface : IUnknown {
   HRESULT mf(int a);
};

HRESULT IMyInterface::mf(int a) {}   // C2861

```