---
title: Kompilator ostrzeżenie (poziom 4) C4214
ms.date: 11/04/2016
f1_keywords:
- C4214
helpviewer_keywords:
- C4214
ms.assetid: 9b8db279-1f12-4a6b-a923-2db22acd1947
ms.openlocfilehash: 31711d3709b7c2ae3658d760f538ea9e841d33a6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401127"
---
# <a name="compiler-warning-level-4-c4214"></a>Kompilator ostrzeżenie (poziom 4) C4214

użyto niestandardowego rozszerzenia: typy pól inne niż int bitowych

Za pomocą rozszerzenia Microsoft do domyślnego (/Ze) elementy członkowskie struktury bitfield może być dowolnego typu liczby całkowitej.

## <a name="example"></a>Przykład

```
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

Takie pola bitowe są nieprawidłowe w obszarze zgodności ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)).