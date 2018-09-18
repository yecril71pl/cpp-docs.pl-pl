---
title: Błąd kompilatora C3539 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3539
dev_langs:
- C++
helpviewer_keywords:
- C3539
ms.assetid: 34a33a0f-d1b6-498f-b312-ffad2d4799b3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4b2f78b69e00290dcc283e3fc340d25a4a071776
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46091884"
---
# <a name="compiler-error-c3539"></a>Błąd kompilatora C3539

"type": argument szablonu nie może być typem zawierającym "auto"

Typ argumentu wskazanego szablonu nie może zawierać użycie `auto` — słowo kluczowe.

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

1. Nie określaj argument szablonu, za pomocą `auto` — słowo kluczowe.

## <a name="example"></a>Przykład

Poniższy przykład daje C3539.

```
// C3539.cpp
// Compile with /Zc:auto
template<class T> class C{};
int main()
{
   C<auto> c;   // C3539
   return 0;
}
```

## <a name="see-also"></a>Zobacz też

[Auto, słowo kluczowe](../../cpp/auto-keyword.md)