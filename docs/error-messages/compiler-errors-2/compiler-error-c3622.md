---
title: Błąd kompilatora C3622
ms.date: 11/04/2016
f1_keywords:
- C3622
helpviewer_keywords:
- C3622
ms.assetid: 02836f78-0cf2-4947-b87e-710187d81014
ms.openlocfilehash: 69565a1a2d159623bca927a94543834d18c13299
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50518095"
---
# <a name="compiler-error-c3622"></a>Błąd kompilatora C3622

"class": klasy zadeklarowanej jako "— słowo kluczowe" nie można utworzyć wystąpienia

Nastąpiła próba tworzenia wystąpienia klasy oznaczonej jako [abstrakcyjne](../../windows/abstract-cpp-component-extensions.md). Klasa jest oznaczona jako `abstract` może być klasą bazową, ale nie można utworzyć wystąpienia.

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
