---
title: Błąd kompilatora C2847 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2847
dev_langs:
- C++
helpviewer_keywords:
- C2847
ms.assetid: 9ad9a0e0-8b16-49d9-a5be-f8eda2372aa9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 41e3b49c509240fd0d782aacaa9fae836b62702a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46054444"
---
# <a name="compiler-error-c2847"></a>Błąd kompilatora C2847

Nie można zastosować operatora sizeof do zarządzanych lub typu WinRT "class"

[Sizeof](../../cpp/sizeof-operator.md) operator pobiera wartości obiektu w czasie kompilacji. Rozmiar zarządzanej lub klasa WinRT, interfejsu lub typu wartości jest dynamiczny, a więc nie może być znane w czasie kompilacji.

Na przykład poniższy przykład spowoduje wygenerowanie C2847:

```
// C2847.cpp
// compile with: /clr
ref class A {};

int main() {
   A ^ xA = gcnew A;
   sizeof(*xA);   // C2847 cannot use sizeof on managed object
}
```
