---
title: Ostrzeżenie kompilatora (poziom 1) C4129
ms.date: 11/04/2016
f1_keywords:
- C4129
helpviewer_keywords:
- C4129
ms.assetid: a4190c64-4bfb-48fd-8e98-52720bc0d878
ms.openlocfilehash: 1a48fc806f3274a59c99be25ac7a0e7b03a0454b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80176224"
---
# <a name="compiler-warning-level-1-c4129"></a>Ostrzeżenie kompilatora (poziom 1) C4129

"Character": nierozpoznany znak sekwencji ucieczki

`character` po ukośniku odwrotnym (\\) w znaku lub stałej ciągu nie jest rozpoznawana jako prawidłowa sekwencja ucieczki. Ukośnik odwrotny jest ignorowany i nie jest drukowany. Zostanie wydrukowany znak następujący po ukośniku odwrotnym.

Aby wydrukować pojedynczy ukośnik odwrotny, określ podwójny ukośnik odwrotny (\\\\).

C++ Standard, w sekcji 2.13.2, omawia sekwencje ucieczki.

Poniższy przykład generuje C4129:

```cpp
// C4129.cpp
// compile with: /W1
int main() {
   char array1[] = "\/709";   // C4129
   char array2[] = "\n709";   // OK
}
```
