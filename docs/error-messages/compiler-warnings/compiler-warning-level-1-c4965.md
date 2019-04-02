---
title: Kompilator ostrzeżenie (poziom 1) C4965
ms.date: 11/04/2016
f1_keywords:
- C4965
helpviewer_keywords:
- C4965
ms.assetid: 47f3f6dc-459b-4a25-9947-f394c8966cb5
ms.openlocfilehash: 2e93fdeba7f9b5b10340ccd1920807a3fcb345a0
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58771061"
---
# <a name="compiler-warning-level-1-c4965"></a>Kompilator ostrzeżenie (poziom 1) C4965

niejawne rzutowanie liczby całkowitej 0; Użyj nullptr lub jawnego rzutowania

Visual C++ funkcje niejawna konwersja boxing typów wartości. Instrukcji, która spowodowała przypisanie wartości null, przy użyciu zarządzanych rozszerzeń języka C++ teraz staje się przypisania do spakowanej int.

Aby uzyskać więcej informacji, zobacz [pakowania](../../extensions/boxing-cpp-component-extensions.md).

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C4965.

```
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