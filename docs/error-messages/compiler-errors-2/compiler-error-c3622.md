---
title: Błąd kompilatora C3622
ms.date: 11/04/2016
f1_keywords:
- C3622
helpviewer_keywords:
- C3622
ms.assetid: 02836f78-0cf2-4947-b87e-710187d81014
ms.openlocfilehash: 2adcee4cb20c39c39b06e0ac2087478cfe2d8937
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74740900"
---
# <a name="compiler-error-c3622"></a>Błąd kompilatora C3622

"Class": nie można utworzyć wystąpienia klasy zadeklarowanej jako "słowo kluczowe"

Podjęto próbę utworzenia wystąpienia klasy oznaczonej jako [abstrakcyjna](../../extensions/abstract-cpp-component-extensions.md). Klasa oznaczona jako `abstract` może być klasą bazową, ale nie można jej utworzyć.

## <a name="example"></a>Przykład

Poniższy przykład generuje C3622.

```cpp
// C3622.cpp
// compile with: /clr
ref class a abstract {};

int main() {
   a aa;   // C3622
}
```
