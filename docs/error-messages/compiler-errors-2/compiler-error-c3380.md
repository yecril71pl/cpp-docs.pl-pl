---
title: Błąd kompilatora C3380
ms.date: 11/04/2016
f1_keywords:
- C3380
helpviewer_keywords:
- C3380
ms.assetid: 86f1f4ec-4ad8-4a1a-9b6c-2d9b6129df6b
ms.openlocfilehash: 516690f2524d48e7abbf7546592c6346e92c3e2e
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59778868"
---
# <a name="compiler-error-c3380"></a>Błąd kompilatora C3380

"class": Nieprawidłowy specyfikator dostępu do zestawu - tylko "public" lub "private" są dozwolone

Po zastosowaniu do zarządzanej klasy lub struktury, [publicznych](../../cpp/public-cpp.md) i [prywatnej](../../cpp/private-cpp.md) słowa kluczowe wskazuje, czy klasa będzie udostępniana przez metadane zestawu. Tylko `public` lub `private` mogą być stosowane do klasy w programie skompilowany przy użyciu [/CLR](../../build/reference/clr-common-language-runtime-compilation.md).

`ref` i `value` słów kluczowych, gdy jest używane z [/CLR](../../build/reference/clr-common-language-runtime-compilation.md), wskazują, że klasa jest zarządzana (zobacz [klas i struktur](../../extensions/classes-and-structs-cpp-component-extensions.md)).

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
