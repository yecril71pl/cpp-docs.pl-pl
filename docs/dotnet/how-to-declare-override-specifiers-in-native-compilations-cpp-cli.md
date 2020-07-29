---
title: 'Instrukcje: deklarowanie specyfikatorów przesłonięć (C++/CLI)'
ms.date: 11/04/2016
helpviewer_keywords:
- override specifiers in native compilation, overriding
ms.assetid: d0551836-9ac7-41eb-a6e9-a4b3ef60767d
ms.openlocfilehash: c5ed413f403fb12f116633c0e39f9e7b32b2e9f8
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221331"
---
# <a name="how-to-declare-override-specifiers-in-native-compilations-ccli"></a>Porady: deklarowanie specyfikatorów przesłonięć w kompilacjach kodu natywnego (C++/CLI)

[zapieczętowane](../extensions/sealed-cpp-component-extensions.md), [abstrakcyjne](../extensions/abstract-cpp-component-extensions.md)i [przesłonięcia](../extensions/override-cpp-component-extensions.md) są dostępne w kompilacjach, które nie używają **/zw** lub [/CLR](../build/reference/clr-common-language-runtime-compilation.md).

> [!NOTE]
> Język standardowy ISO C++ 11 ma identyfikator [przesłonięcia](../cpp/override-specifier.md) i [końcowy](../cpp/final-specifier.md) identyfikator, a oba są obsługiwane w programie Visual Studio `final` , a nie **`sealed`** w kodzie, który jest przeznaczony do skompilowania jako tylko natywny.

## <a name="example"></a>Przykład

### <a name="description"></a>Opis

Poniższy przykład pokazuje, że **`sealed`** jest prawidłowy w kompilacjach natywnych.

### <a name="code"></a>Kod

```cpp
// sealed_native_keyword.cpp
#include <stdio.h>
__interface I1 {
   virtual void f();
   virtual void g();
};

class X : public I1 {
public:
   virtual void g() sealed {}
};

class Y : public X {
public:

   // the following override generates a compiler error
   virtual void g() {}   // C3248 X::g is sealed!
};
```

## <a name="example"></a>Przykład

### <a name="description"></a>Opis

Następny przykład pokazuje, że `override` jest prawidłowy w kompilacjach natywnych.

### <a name="code"></a>Kod

```cpp
// override_native_keyword.cpp
#include <stdio.h>
__interface I1 {
   virtual void f();
};

class X : public I1 {
public:
   virtual void f() override {}   // OK
   virtual void g() override {}   // C3668 I1::g does not exist
};
```

## <a name="example"></a>Przykład

### <a name="description"></a>Opis

Ten przykład pokazuje, że **`abstract`** jest prawidłowy w kompilacjach natywnych.

### <a name="code"></a>Kod

```cpp
// abstract_native_keyword.cpp
class X abstract {};

int main() {
   X * MyX = new X;   // C3622 cannot instantiate abstract class
}
```

## <a name="see-also"></a>Zobacz także

[Specyfikatory przesłonięcia](../extensions/override-specifiers-cpp-component-extensions.md)
