---
title: Błąd kompilatora C3553
ms.date: 11/04/2016
f1_keywords:
- C3553
helpviewer_keywords:
- C3553
ms.assetid: 7f84bf37-6419-4ad3-ab30-64266100b930
ms.openlocfilehash: 82540e0f6c4b60aea2e708dcf00796490cd7d3cc
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80200658"
---
# <a name="compiler-error-c3553"></a>Błąd kompilatora C3553

> decltype oczekuje wyrażenia, a nie typu

Słowo kluczowe `decltype()` wymaga wyrażenia jako argumentu, a nie nazwy typu. Na przykład ostatnią instrukcją w poniższym fragmencie kodu jest zwrócenie błędu C3553.

```cpp
int x = 0;
decltype(x+1);
decltype(int); // C3553
```
