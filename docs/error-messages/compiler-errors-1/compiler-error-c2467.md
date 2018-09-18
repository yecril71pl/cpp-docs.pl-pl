---
title: Błąd kompilatora C2467 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2467
dev_langs:
- C++
helpviewer_keywords:
- C2467
ms.assetid: f9ead270-5d0b-41cc-bdcd-586a647c67a7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8bab320bfdba9fcbd408771b7859a22fc85fa06e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46048778"
---
# <a name="compiler-error-c2467"></a>Błąd kompilatora C2467

Niedozwolona deklaracja anonimowych "użytkownik zdefiniowane type"

Zagnieżdżony typ zdefiniowany przez użytkownika został zadeklarowany. Jest to błąd, podczas kompilowania kodu źródłowego języka C z opcją zgodność ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)) włączone.

Poniższy przykład spowoduje wygenerowanie C2467:

```
//C2467.c
// compile with: /Za
int main() {
   struct X {
      union { int i; };   // C2467, nested declaration
   };
}
```