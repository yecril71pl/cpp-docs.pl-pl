---
title: Błąd kompilatora C3239 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3239
dev_langs:
- C++
helpviewer_keywords:
- C3239
ms.assetid: 22a518b7-020f-4f3c-9963-a094667fd1ac
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7f1d3c405e7a74dbade84b0ecd25284c4d6d8f27
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46093857"
---
# <a name="compiler-error-c3239"></a>Błąd kompilatora C3239

"type": wskaźnik do wskaźnika wnętrza/pin jest zabroniona przez środowisko uruchomieniowe języka wspólnego

Kompilator napotkał nieprawidłowego typu.

Poniższy przykład spowoduje wygenerowanie C3229:

```
// C3239.cpp
// compile with: /clr
int main() {
   interior_ptr<int>* pip0;   // C3239

   // OK
   int * pip1;
   interior_ptr<int> pip2;
   int ** pip;
}
```