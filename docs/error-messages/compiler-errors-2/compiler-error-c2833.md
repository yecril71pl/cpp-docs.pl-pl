---
title: Błąd kompilatora C2833 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2833
dev_langs:
- C++
helpviewer_keywords:
- C2833
ms.assetid: b9418ce1-e2ee-4599-8959-6fde89c27569
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 53360c1eaf81ad407589fbdb125d9e6fe017708e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46070174"
---
# <a name="compiler-error-c2833"></a>Błąd kompilatora C2833

"operator operator" nie jest rozpoznany jako operator lub typ

Wyraz `operator` musi następować operatora, który chcesz przesłonić lub typu, który ma zostać przekonwertowany.

Aby uzyskać listę operatorów, które można zdefiniować w typ zarządzany, zobacz [zdefiniowane przez użytkownika operatory](../../dotnet/user-defined-operators-cpp-cli.md).

Poniższy przykład spowoduje wygenerowanie C2833:

```
// C2833.cpp
// compile with: /c
class A {};

void operator ::* ();   // C2833
void operator :: ();   // OK
```