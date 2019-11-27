---
title: Ostrzeżenie kompilatora (poziom 4) C4214
ms.date: 11/04/2016
f1_keywords:
- C4214
helpviewer_keywords:
- C4214
ms.assetid: 9b8db279-1f12-4a6b-a923-2db22acd1947
ms.openlocfilehash: 85f37810708eff43574129f42dd8444fe7dc37c2
ms.sourcegitcommit: 3ee06ec53153cf21910fc8cfef78a4f25f9633f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/26/2019
ms.locfileid: "74541902"
---
# <a name="compiler-warning-level-4-c4214"></a>Ostrzeżenie kompilatora (poziom 4) C4214

użyto niestandardowego rozszerzenia: typy pól bitowych inne niż int

Z domyślnymi rozszerzeniami Microsoft (/ze), składowe struktury pole bitowe mogą być dowolnego typu Integer.

## <a name="example"></a>Przykład

```c
// C4214.c
// compile with: /W4
struct bitfields
{
   unsigned short j:4;  // C4214
};

int main()
{
}
```

Takie pola bitowe są nieprawidłowe pod kątem zgodności ANSI ([/za](../../build/reference/za-ze-disable-language-extensions.md)).