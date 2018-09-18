---
title: Kompilator ostrzeżenie (poziom 4) C4221 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4221
dev_langs:
- C++
helpviewer_keywords:
- C4221
ms.assetid: 8532bd68-54dc-4526-8597-f61dcb0a0129
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 18b0804c8b7cb2d059e45fa504334687a796fbe1
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46056420"
---
# <a name="compiler-warning-level-4-c4221"></a>Kompilator ostrzeżenie (poziom 4) C4221

użyto niestandardowego rozszerzenia: 'Identyfikator': nie można zainicjować przy użyciu adresu automatycznej zmiennej

Za pomocą domyślnego rozszerzenia Microsoft (/Ze), można inicjować odpowiedni typ agregacji (**tablicy**, `struct`, lub **Unii**) przy użyciu adresu zmiennej lokalnej (automatyczne).

## <a name="example"></a>Przykład

```
// C4221.c
// compile with: /W4
struct S
{
   int *i;
};

void func()
{
   int j;
   struct S s1 = { &j };   // C4221
}

int main()
{
}
```

Takie inicjalizacje są nieprawidłowe w obszarze zgodności ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)).