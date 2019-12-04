---
title: Błąd kompilatora C2728
ms.date: 11/04/2016
f1_keywords:
- C2728
helpviewer_keywords:
- C2728
ms.assetid: 65635f91-1cd1-46e4-9ad7-14726d0546af
ms.openlocfilehash: ac9efa88fc4ab17a656172c44de2e49e82108108
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755671"
---
# <a name="compiler-error-c2728"></a>Błąd kompilatora C2728

"Type": natywna tablica nie może zawierać tego typu

Składnia tworzenia tablicy została użyta do utworzenia tablicy obiektów zarządzanych lub WinRT. Nie można utworzyć tablicy obiektów zarządzanych lub WinRT przy użyciu natywnej składni tablicy.

Aby uzyskać więcej informacji, zobacz [Array](../../extensions/arrays-cpp-component-extensions.md).

Poniższy przykład generuje C2728 i pokazuje, jak to naprawić:

```cpp
// C2728.cpp
// compile with: /clr

int main() {
   int^ arr[5];   // C2728

   // try the following line instead
   array<int>^arr2;
}
```
