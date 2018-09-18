---
title: Błąd kompilatora C3380 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3380
dev_langs:
- C++
helpviewer_keywords:
- C3380
ms.assetid: 86f1f4ec-4ad8-4a1a-9b6c-2d9b6129df6b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e35c4edaf24aacbd7eb9938a1dea2c470d32caae
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46062595"
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
