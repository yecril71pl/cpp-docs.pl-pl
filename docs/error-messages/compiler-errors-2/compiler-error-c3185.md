---
title: Błąd kompilatora C3185 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3185
dev_langs:
- C++
helpviewer_keywords:
- C3185
ms.assetid: 5bf96279-043c-4981-9d02-b4550071b192
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fd7f94f86165fdfd25bb5a901cdb4349a0e48494
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46044525"
---
# <a name="compiler-error-c3185"></a>Błąd kompilatora C3185

"typeid" używane z zarządzanych lub typu WinRT "type", zamiast tego użyj "operator"

Nie można zastosować [typeid](../../cpp/typeid-operator.md) operator ma być zarządzany lub WinRT typu; użyj [typeid](../../windows/typeid-cpp-component-extensions.md) zamiast tego.

Poniższy przykład generuje C3185 i pokazuje, jak go naprawić:

```
// C3185a.cpp
// compile with: /clr
ref class Base {};
ref class Derived : public Base {};

int main() {
   Derived ^ pd = gcnew Derived;
   Base ^pb = pd;
   const type_info & t1 = typeid(pb);   // C3185
   System::Type ^ MyType = Base::typeid;   // OK
};
```
