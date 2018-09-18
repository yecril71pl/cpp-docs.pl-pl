---
title: Błąd kompilatora C2728 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2728
dev_langs:
- C++
helpviewer_keywords:
- C2728
ms.assetid: 65635f91-1cd1-46e4-9ad7-14726d0546af
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fe901a5798028378e6d84a807826b42cae0d64d8
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46036172"
---
# <a name="compiler-error-c2728"></a>Błąd kompilatora C2728

"type": natywna tablica nie może zawierać tego typu

Składni tworzenia tablicy został użyty do utworzenia tablicy zarządzanych lub obiekty WinRT. Nie można utworzyć tablicę zarządzanych lub obiekty WinRT, za pomocą składni tablicy natywnej.

Aby uzyskać więcej informacji, zobacz [tablicy](../../windows/arrays-cpp-component-extensions.md).

Poniższy przykład generuje C2728 i pokazuje, jak go naprawić:

```
// C2728.cpp
// compile with: /clr

int main() {
   int^ arr[5];   // C2728

   // try the following line instead
   array<int>^arr2;
}
```
