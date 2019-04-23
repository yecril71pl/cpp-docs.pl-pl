---
title: Błąd kompilatora C2728
ms.date: 11/04/2016
f1_keywords:
- C2728
helpviewer_keywords:
- C2728
ms.assetid: 65635f91-1cd1-46e4-9ad7-14726d0546af
ms.openlocfilehash: 1fbbc3d63386ebe98a447de8b7166a5263d2168f
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59778790"
---
# <a name="compiler-error-c2728"></a>Błąd kompilatora C2728

"type": natywna tablica nie może zawierać tego typu

Składni tworzenia tablicy został użyty do utworzenia tablicy zarządzanych lub obiekty WinRT. Nie można utworzyć tablicę zarządzanych lub obiekty WinRT, za pomocą składni tablicy natywnej.

Aby uzyskać więcej informacji, zobacz [tablicy](../../extensions/arrays-cpp-component-extensions.md).

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
