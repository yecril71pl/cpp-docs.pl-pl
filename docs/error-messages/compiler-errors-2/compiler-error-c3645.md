---
title: Błąd kompilatora C3645 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3645
dev_langs:
- C++
helpviewer_keywords:
- C3645
ms.assetid: 346da528-ae86-4cd0-9654-f41bee26ac0d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2d310ab3a9a4bd0b31b9e6295a93a571a54f585b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46068913"
---
# <a name="compiler-error-c3645"></a>Błąd kompilatora C3645

'Funkcja': __clrcall nie można używać w funkcjach skompilowanych do natywnego kodu

Obecność niektórych słów kluczowych w funkcji spowoduje, że funkcja jest kompilowana do natywnego.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C3645.

```
// C3645.cpp
// compile with: /clr /c
#pragma unmanaged
int __clrcall dog() {}   // C3645
```