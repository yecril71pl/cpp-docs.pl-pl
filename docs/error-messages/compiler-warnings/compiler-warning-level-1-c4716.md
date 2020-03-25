---
title: Ostrzeżenie kompilatora (poziom 1) C4716
ms.date: 11/04/2016
f1_keywords:
- C4716
helpviewer_keywords:
- C4716
ms.assetid: d95ecfe5-870f-461f-a746-7913af98414b
ms.openlocfilehash: 91e836c9bb606d7759206788d1e3abd63b293fa8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175314"
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
