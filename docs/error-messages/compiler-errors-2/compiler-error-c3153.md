---
title: Błąd kompilatora C3153 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3153
dev_langs:
- C++
helpviewer_keywords:
- C3153
ms.assetid: d775d97e-2480-484f-81f1-88406b10f947
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 621af32475008eda4d7502530087673dcb4a0848
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46016043"
---
# <a name="compiler-error-c3153"></a>Błąd kompilatora C3153

"interface": nie można utworzyć instancji interfejsu

Nie można utworzyć wystąpienia interfejsu. Aby korzystać z elementów członkowskich interfejsu, wyprowadzić klasę z interfejsu, implementowanie elementów interfejsu, a następnie używać elementów członkowskich.

Poniższy przykład spowoduje wygenerowanie C3153:

```
// C3153.cpp
// compile with: /clr
interface class A {
};

int main() {
   A^ a = gcnew A;   // C3153
}
```
