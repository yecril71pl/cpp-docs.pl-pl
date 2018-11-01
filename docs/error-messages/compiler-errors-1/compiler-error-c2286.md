---
title: Błąd kompilatora C2286
ms.date: 11/04/2016
f1_keywords:
- C2286
helpviewer_keywords:
- C2286
ms.assetid: 078e0201-35cc-42e2-8dbc-6f8cf557b098
ms.openlocfilehash: 7d3b8297c5f5da29b99abe78999396e8c44df0fd
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50667509"
---
# <a name="compiler-error-c2286"></a>Błąd kompilatora C2286

wskaźniki do składowych reprezentacji w postaci 'Identyfikator' jest już ustawiona na "dziedziczenia" — deklaracja ignorowana

Istnieją dwa różne reprezentacje wskaźników do elementów członkowskich dla klasy.

Aby uzyskać więcej informacji, zobacz [słowa kluczowe dziedziczenia](../../cpp/inheritance-keywords.md).

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C2286:

```
// C2286.cpp
// compile with: /c
class __single_inheritance X;
class __multiple_inheritance X;   // C2286
class  __multiple_inheritance Y;   // OK
```