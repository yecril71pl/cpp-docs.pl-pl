---
title: Błąd kompilatora C3083 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3083
dev_langs:
- C++
helpviewer_keywords:
- C3083
ms.assetid: 05ff791d-52bb-41eb-9511-3ef89d7f4710
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 28bc0a42aa6f6f59c9241a615764b474b23957b1
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46091640"
---
# <a name="compiler-error-c3083"></a>Błąd kompilatora C3083

'Funkcja': symbol po lewej stronie "::" musi być typem

Funkcja została niepoprawnie wywołana.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C3083.

```
// C3083.cpp
// compile with: /c
struct N {
   ~N();
};

struct N1 {
   ~N1();
};

N::N::~N() {}   // C3083
N1::~N1() {}   // OK
```