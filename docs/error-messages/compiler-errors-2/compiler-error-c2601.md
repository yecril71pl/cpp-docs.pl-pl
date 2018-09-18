---
title: Błąd kompilatora C2601 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2601
dev_langs:
- C++
helpviewer_keywords:
- C2601
ms.assetid: 88275582-5f37-45d7-807d-05f06ba00965
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 522abe9c3cb4b9922a6b307055a3d85f40253793
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46062959"
---
# <a name="compiler-error-c2601"></a>Błąd kompilatora C2601

'Funkcja': definicje funkcji lokalnych są niedozwolone

Kod próbuje zdefiniować funkcję w funkcji.

Lub w kodzie źródłowym przed lokalizacji błędu C2601 może być dodatkowe nawiasu klamrowego.

Poniższy przykład spowoduje wygenerowanie C2601:

```
// C2601.cpp
int main() {
   int i = 0;

   void funcname(int j) {   // C2601
      j++;
   }
}
```