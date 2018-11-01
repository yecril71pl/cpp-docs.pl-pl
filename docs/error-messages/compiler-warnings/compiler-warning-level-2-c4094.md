---
title: Kompilator ostrzeżenie (poziom 2) C4094
ms.date: 11/04/2016
f1_keywords:
- C4094
helpviewer_keywords:
- C4094
ms.assetid: e68929fb-3a1c-4be7-920b-d5f79f534f99
ms.openlocfilehash: 73805afc897d14c6d2cc87490dfa0769a8de5193
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50488403"
---
# <a name="compiler-warning-level-2-c4094"></a>Kompilator ostrzeżenie (poziom 2) C4094

nieoznakowany "token" nie zadeklarował żadnych symboli

Kompilator wykrył pusta deklaracja, za pomocą nieoznakowany struktura, Unia lub klasa. Deklaracja jest ignorowany.

## <a name="example"></a>Przykład

```
// C4094.cpp
// compile with: /W2
struct
{
};   // C4094

int main()
{
}
```

Ten warunek generuje błąd w obszarze zgodności ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)).