---
title: Ostrzeżenie kompilatora (poziom 1) C4716
ms.date: 11/04/2016
f1_keywords:
- C4716
helpviewer_keywords:
- C4716
ms.assetid: d95ecfe5-870f-461f-a746-7913af98414b
ms.openlocfilehash: 5215e8fd0bdd44c9bdfc731d2b74499d38853e80
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052464"
---
# <a name="compiler-warning-level-1-c4716"></a>Ostrzeżenie kompilatora (poziom 1) C4716

Funkcja "Function" musi zwracać wartość

Dana funkcja nie zwróciła wartości.

Tylko funkcje z typem zwracanym void mogą używać polecenia Return bez towarzyszącej wartości zwracanej.

Niezdefiniowana wartość zostanie zwrócona, gdy ta funkcja zostanie wywołana.

To ostrzeżenie jest automatycznie podwyższana do błędu. Jeśli chcesz zmodyfikować to zachowanie, użyj [#pragma ostrzeżenie](../../preprocessor/warning.md).

Poniższy przykład generuje C4716:

```cpp
// C4716.cpp
// compile with: /c /W1
// C4716 expected
#pragma warning(default:4716)
int test() {
   // uncomment the following line to resolve
   // return 0;
}
```