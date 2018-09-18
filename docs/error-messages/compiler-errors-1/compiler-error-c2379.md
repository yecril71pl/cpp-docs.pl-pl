---
title: Błąd kompilatora C2379 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2379
dev_langs:
- C++
helpviewer_keywords:
- C2379
ms.assetid: 37dc3015-a4af-4341-bbf3-da6150df7e51
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ec340a5a48705eb91bf5bf72ec20ad382f4b262c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46032448"
---
# <a name="compiler-error-c2379"></a>Błąd kompilatora C2379

Liczba parametrów formalnych ma innego typu kiedy jest zwiększany

Typ określony parametr nie jest zgodne, za pośrednictwem promocji domyślnej z typem w poprzedniej deklaracji. Jest to błąd w ANSI C ([/Za](../../build/reference/za-ze-disable-language-extensions.md)) i ostrzeżenia z rozszerzeniami firmy Microsoft (**/Ze**).

Poniższy przykład spowoduje wygenerowanie C2379:

```
// C2379.c
// compile with: /Za
void func();
void func(char);   // C2379, char promotes to int
```