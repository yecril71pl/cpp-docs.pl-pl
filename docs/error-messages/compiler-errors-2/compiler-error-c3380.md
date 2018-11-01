---
title: Błąd kompilatora C3380
ms.date: 11/04/2016
f1_keywords:
- C3380
helpviewer_keywords:
- C3380
ms.assetid: 86f1f4ec-4ad8-4a1a-9b6c-2d9b6129df6b
ms.openlocfilehash: e03212c3148ba7f5c445dfee02ee32629ab5d373
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50668588"
---
# <a name="compiler-error-c3380"></a>Błąd kompilatora C3380

"class": Nieprawidłowy specyfikator dostępu do zestawu - tylko "public" lub "private" są dozwolone

Po zastosowaniu do zarządzanej klasy lub struktury, [publicznych](../../cpp/public-cpp.md) i [prywatnej](../../cpp/private-cpp.md) słowa kluczowe wskazuje, czy klasa będzie udostępniana przez metadane zestawu. Tylko `public` lub `private` mogą być stosowane do klasy w programie skompilowany przy użyciu [/CLR](../../build/reference/clr-common-language-runtime-compilation.md).

`ref` i `value` słów kluczowych, gdy jest używane z [/CLR](../../build/reference/clr-common-language-runtime-compilation.md), wskazują, że klasa jest zarządzana (zobacz [klas i struktur](../../windows/classes-and-structs-cpp-component-extensions.md)).

Poniższy przykład spowoduje wygenerowanie C3380:

```
// C3380_2.cpp
// compile with: /clr
protected ref class A {   // C3380
// try the following line instead
// ref class A {
public:
   static int i = 9;
};

int main() {
   A^ myA = gcnew A;
   System::Console::WriteLine(myA->i);
}
```
