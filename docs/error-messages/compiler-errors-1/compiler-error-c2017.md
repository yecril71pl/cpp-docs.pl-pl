---
title: Błąd kompilatora C2017 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2017
dev_langs:
- C++
helpviewer_keywords:
- C2017
ms.assetid: 1083eed9-9906-4a97-883c-54e52d7e82cd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f547501ab399165fe256f0dc3d0423b3569c05e7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46062205"
---
# <a name="compiler-error-c2017"></a>Błąd kompilatora C2017

Niedozwolona sekwencja ucieczki

Sekwencja wyjścia, takich jak \t, pojawia się poza znak lub ciąg stałej.

Poniższy przykład spowoduje wygenerowanie C2017:

```
// C2017.cpp
int main() {
   char test1='a'\n;   // C2017
   char test2='a\n';   // ok
}
```

C2017 może wystąpić, gdy stringize operator jest używany z ciągów, które zawierają sekwencje ucieczki.

Poniższy przykład spowoduje wygenerowanie C2017:

```
// C2017b.cpp
#define TestDfn(x) AfxMessageBox(#x)
TestDfn(CString("\\") + CString(".h\"\n\n"));   // C2017
```