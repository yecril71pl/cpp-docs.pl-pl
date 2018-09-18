---
title: Błąd kompilatora C3623 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3623
dev_langs:
- C++
helpviewer_keywords:
- C3623
ms.assetid: a0341b45-062a-4f67-beb9-ba74201ed1ed
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 90198a3ea7cfb96b75717550b551c55915187211
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46085306"
---
# <a name="compiler-error-c3623"></a>Błąd kompilatora C3623

'Zmienna': pola bitowe nie są obsługiwane w zarządzanych lub typów WinRT

Użyj pól bitowych nie jest dozwolona w zmiennych w zarządzanej lub klasa WinRT.

Poniższy przykład spowoduje wygenerowanie C3623:

```
// C3623.cpp
// compile with: /clr
using namespace System;
ref class CMyClass {
public:
   int i : 1;   // C3623
};

int main() {
   CMyClass^ pMyClass = gcnew CMyClass();
   pMyClass->i = 3;
   Console::Out->WriteLine(pMyClass->i);
}
```
