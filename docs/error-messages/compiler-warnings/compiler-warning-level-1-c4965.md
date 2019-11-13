---
title: Ostrzeżenie kompilatora (poziom 1) C4965
ms.date: 11/04/2016
f1_keywords:
- C4965
helpviewer_keywords:
- C4965
ms.assetid: 47f3f6dc-459b-4a25-9947-f394c8966cb5
ms.openlocfilehash: ac1ffc1626a8b72fd7c9026afb6c6a54bace3750
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052233"
---
# <a name="compiler-warning-level-1-c4965"></a>Ostrzeżenie kompilatora (poziom 1) C4965

niejawne pole z liczbą całkowitą 0; Użyj nullptr lub jawnego rzutowania

Funkcje C++ wizualne niejawnego pakowania typów wartości. Instrukcja, która spowodowała przypisanie wartości null przy użyciu rozszerzeń zarządzanych dla C++ teraz, zostaje przypisana do opakowanej int.

Aby uzyskać więcej informacji, zobacz [opakowanie](../../extensions/boxing-cpp-component-extensions.md).

## <a name="example"></a>Przykład

Poniższy przykład generuje C4965.

```cpp
// C4965.cpp
// compile with: /clr /W1
int main() {
   System::Object ^o = 0;   // C4965

   // the previous line is the same as the following line
   // using Managed Extensions for C++
   // System::Object *o = __box(0);

   // OK
   System::Object ^o2 = nullptr;
   System::Object ^o3 = safe_cast<System::Object^>(0);
}
```