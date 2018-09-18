---
title: Błąd kompilatora C2390 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2390
dev_langs:
- C++
helpviewer_keywords:
- C2390
ms.assetid: 06b749ee-d072-4db1-b229-715f2c0728b5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5de5a9af8f8aa04219f0a7d61162336745fd4bfa
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46098217"
---
# <a name="compiler-error-c2390"></a>Błąd kompilatora C2390

'Identyfikator': niepoprawna Klasa magazynu "specyfikatora"

Klasa magazynu nie jest prawidłowy dla identyfikatora zakresu globalnego. Domyślna klasa magazynu jest używany zamiast nieprawidłowa klasa.

Możliwe rozwiązania:

- Jeśli identyfikator jest funkcją, Zadeklaruj go `extern` magazynu.

- Jeśli identyfikator jest formalny parametr lub zmienna lokalna, Zadeklaruj go z usługą storage automatycznie.

- Jeśli identyfikator jest zmienną globalną, Zadeklaruj go za pomocą nie klasy magazynu (auto magazynu).

## <a name="example"></a>Przykład

- Poniższy przykład spowoduje wygenerowanie C2390:

```
// C2390.cpp
register int i;   // C2390

int main() {
   register int j;   // OK
}
```