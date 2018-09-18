---
title: Błąd kompilatora C2563 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2563
dev_langs:
- C++
helpviewer_keywords:
- C2563
ms.assetid: 54abba68-6458-4ca5-894d-3babdb7b3552
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: eec8526df1c5ff69899dd0a2d103cb5f28d4c00c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46067407"
---
# <a name="compiler-error-c2563"></a>Błąd kompilatora C2563

niezgodność w liście formalnych parametrów

Lista parametrów formalnych funkcji (lub wskaźnik do funkcji) nie odpowiadają innej funkcji (lub wskaźnika do funkcji składowej). W rezultacie nie można wykonać przypisania funkcji lub wskaźników.

Poniższy przykład spowoduje wygenerowanie C2563:

```
// C2563.cpp
void func( int );
void func( int, int );
int main() {
   void *fp();
   fp = func;   // C2563
}
```