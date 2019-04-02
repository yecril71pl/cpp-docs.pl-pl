---
title: Błąd kompilatora C3622
ms.date: 11/04/2016
f1_keywords:
- C3622
helpviewer_keywords:
- C3622
ms.assetid: 02836f78-0cf2-4947-b87e-710187d81014
ms.openlocfilehash: ed307f46db1261d79d5b0ec6b36852cac2e6d13e
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58781916"
---
# <a name="compiler-error-c3622"></a>Błąd kompilatora C3622

"class": klasy zadeklarowanej jako "— słowo kluczowe" nie można utworzyć wystąpienia

Nastąpiła próba tworzenia wystąpienia klasy oznaczonej jako [abstrakcyjne](../../extensions/abstract-cpp-component-extensions.md). Klasa jest oznaczona jako `abstract` może być klasą bazową, ale nie można utworzyć wystąpienia.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C3622.

```
// C3622.cpp
// compile with: /clr
ref class a abstract {};

int main() {
   a aa;   // C3622
}
```
