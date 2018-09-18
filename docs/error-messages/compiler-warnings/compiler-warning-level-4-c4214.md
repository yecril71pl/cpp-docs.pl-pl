---
title: Kompilator ostrzeżenie (poziom 4) C4214 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4214
dev_langs:
- C++
helpviewer_keywords:
- C4214
ms.assetid: 9b8db279-1f12-4a6b-a923-2db22acd1947
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 879c959bfe851b56dbc60b4eeb714db8d7f9dfaf
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46027430"
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