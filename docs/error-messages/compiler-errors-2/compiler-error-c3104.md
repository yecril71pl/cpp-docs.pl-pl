---
title: Błąd kompilatora C3104 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3104
dev_langs:
- C++
helpviewer_keywords:
- C3104
ms.assetid: b5648d47-e5d3-4b45-a3c0-f46e04eae731
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: db9bce4d47658b012824087f62eb55ccd7ddf669
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46111150"
---
# <a name="compiler-error-c3104"></a>Błąd kompilatora C3104

Niedozwolony argument atrybutu

Określono nieprawidłowy argument do atrybutu.

Zobacz [typy parametrów atrybutu](../../windows/attribute-parameter-types-cpp-component-extensions.md) Aby uzyskać więcej informacji.

Ten błąd można wygenerować w wyniku pracy zgodności kompilatora, która została wykonana dla programu Visual C++ 2005: podczas przekazywania tablic do atrybutów niestandardowych, typ tablicy nie jest już jest wyprowadzony z listy inicjowania agregacji. Kompilator teraz wymaga określenia typu tablicy, jak również lista inicjatora.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C3104.

```
// C3104a.cpp
// compile with: /clr /c
using namespace System;

[AttributeUsage(AttributeTargets::Class)]
public ref struct ABC : public Attribute {
   ABC(array<int>^){}
   array<double> ^ param;
};

[ABC( {1,2,3}, param = {2.71, 3.14})]   // C3104
// try the following line instead
// [ABC( gcnew array<int> {1,2,3}, param = gcnew array<double>{2.71, 3.14})]
ref struct AStruct{};
```

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C3104.

```
// C3104b.cpp
// compile with: /clr /c
// C3104 expected
using namespace System;

int func() {
   return 0;
}

[attribute(All)]
ref class A {
public:
   A(int) {}
};

// Delete the following 2 lines to resolve.
[A(func())]
ref class B {};

// OK
[A(0)]
ref class B {};
```
