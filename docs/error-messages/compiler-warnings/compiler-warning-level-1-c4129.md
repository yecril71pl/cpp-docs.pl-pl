---
title: Kompilator ostrzeżenie (poziom 1) C4129 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4129
dev_langs:
- C++
helpviewer_keywords:
- C4129
ms.assetid: a4190c64-4bfb-48fd-8e98-52720bc0d878
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6e02f38044180c45e221099d2874b7f8ff48d62f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46098449"
---
# <a name="compiler-warning-level-1-c4129"></a>Kompilator ostrzeżenie (poziom 1) C4129

"character": nierozpoznany znak sekwencji ucieczki

`character` Ukośniku odwrotnym (\\) znaku lub ciągu stała nie został rozpoznany jako prawidłowy sekwencje. Ukośnik odwrotny jest ignorowane i nie są wyświetlane. Znak po ukośniku odwrotnym jest drukowany.

Aby wydrukować pojedynczy ukośnik odwrotny, należy określić podwójny ukośnik odwrotny (\\\\).

Standard C++, w sekcji 2.13.2 omawia unikowe.

Poniższy przykład spowoduje wygenerowanie C4129:

```
// C4129.cpp
// compile with: /W1
int main() {
   char array1[] = "\/709";   // C4129
   char array2[] = "\n709";   // OK
}
```