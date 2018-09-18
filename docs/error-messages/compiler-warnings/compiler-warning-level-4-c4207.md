---
title: Kompilator ostrzeżenie (poziom 4) C4207 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4207
dev_langs:
- C++
helpviewer_keywords:
- C4207
ms.assetid: f4e09e3e-ac87-4489-8e3f-c8f76b82e721
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a5aa7f364eb8f60d680dde4c252b9c84e258cda0
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46068835"
---
# <a name="compiler-warning-level-4-c4207"></a>Kompilator ostrzeżenie (poziom 4) C4207

użyto niestandardowego rozszerzenia: rozszerzony formularz inicjatora

Rozszerzenia Microsoft (/Ze), można inicjować tablica bez określonego rozmiaru `char` przy użyciu ciągu w nawiasach klamrowych.

## <a name="example"></a>Przykład

```
// C4207.c
// compile with: /W4
char c[] = { 'a', 'b', "cdefg" }; // C4207

int main()
{
}
```

Takie inicjalizacje są nieprawidłowe w obszarze zgodności ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)).