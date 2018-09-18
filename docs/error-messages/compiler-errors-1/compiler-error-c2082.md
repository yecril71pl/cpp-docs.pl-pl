---
title: Błąd kompilatora C2082 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2082
dev_langs:
- C++
helpviewer_keywords:
- C2082
ms.assetid: 87a6d442-157c-46e8-9bff-8388f8338ae0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f6939bf628072fc1c5c4e72c0012e4a190d43864
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46082407"
---
# <a name="compiler-error-c2082"></a>Błąd kompilatora C2082

ponowne zdefiniowanie formalnego parametru 'Identyfikator'

Formalny parametr do funkcji jest ponownie zadeklarowany w treści funkcji. Aby naprawić błąd, należy usunąć ponowne zdefiniowanie.

Poniższy przykład spowoduje wygenerowanie C2082:

```
// C2082.cpp
void func(int i) {
   int i;   // C2082
   int ii;   // OK
}
```