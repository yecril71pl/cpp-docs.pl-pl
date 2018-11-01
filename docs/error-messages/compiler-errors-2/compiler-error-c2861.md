---
title: Błąd kompilatora C2861
ms.date: 11/04/2016
f1_keywords:
- C2861
helpviewer_keywords:
- C2861
ms.assetid: 012bb44d-6c9b-4def-b54e-b19f1f8ddd1b
ms.openlocfilehash: e7cced7a9abd974d0cbcea69059459d6c15f9850
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50514702"
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