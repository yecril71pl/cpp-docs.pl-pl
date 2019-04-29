---
title: Kompilator ostrzeżenie (poziom 2) C4094
ms.date: 11/04/2016
f1_keywords:
- C4094
helpviewer_keywords:
- C4094
ms.assetid: e68929fb-3a1c-4be7-920b-d5f79f534f99
ms.openlocfilehash: 73805afc897d14c6d2cc87490dfa0769a8de5193
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62350520"
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