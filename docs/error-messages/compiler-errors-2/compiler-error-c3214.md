---
title: Błąd kompilatora C3214
ms.date: 11/04/2016
f1_keywords:
- C3214
helpviewer_keywords:
- C3214
ms.assetid: 49ee4a9a-2549-4adb-9d3a-38e154303c2e
ms.openlocfilehash: e4f271ec4abdc05b5cf148e40a752b4d62cc884c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50651181"
---
# <a name="compiler-error-c3214"></a>Błąd kompilatora C3214

"type": nieprawidłowy typ argumentu dla parametru generycznego param, z ogólnego "generic_type" nie spełnia ograniczenia "ograniczenia"

Typ określono podczas tworzenia wystąpienia klasy generycznej, która nie spełnia ograniczenia klasy ogólnej.

Poniższy przykład spowoduje wygenerowanie C3214:

```
// C3214.cpp
// compile with: /clr
interface struct A {};

generic <class T>
where T : A
ref class C {};

ref class X : public A {};

int main() {
   C<int>^ c = new C<int>;   // C3214
   C<X ^> ^ c2 = new C<X^>;   // OK
}
```