---
title: 'Instrukcje: Deklarowanie specyfikatorów przesłonięć (C + +/ CLI)'
ms.date: 11/04/2016
helpviewer_keywords:
- override specifiers in native compilation, overriding
ms.assetid: d0551836-9ac7-41eb-a6e9-a4b3ef60767d
ms.openlocfilehash: db74ef226242ec8f4f70f2769fbc8ba102a808c8
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58777184"
---
# <a name="how-to-declare-override-specifiers-in-native-compilations-ccli"></a>Instrukcje: Deklarowanie specyfikatorów przesłonięć w kompilacjach kodu natywnego (C + +/ CLI)

[zapieczętowane](../extensions/sealed-cpp-component-extensions.md), [abstrakcyjne](../extensions/abstract-cpp-component-extensions.md), i [zastąpienia](../extensions/override-cpp-component-extensions.md) są dostępne w kompilacjach, które nie korzystają z **/ZW** lub [/CLR](../build/reference/clr-common-language-runtime-compilation.md).

> [!NOTE]
>  ISO C ++ 11 standardowy język ma [zastąpienia](../cpp/override-specifier.md) identyfikator i [końcowego](../cpp/final-specifier.md) identyfikator i obie są obsługiwane w Visual Studio użyj `final` zamiast `sealed` w kodzie, który jest przeznaczony do można skompilować jako tylko do natywnego.

## <a name="example"></a>Przykład

### <a name="description"></a>Opis

Poniższy przykład pokazuje, że `sealed` jest prawidłowy w kompilacjach kodu natywnego.

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

Następny przykład pokazuje, że `override` jest prawidłowy w kompilacjach kodu natywnego.

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

Ten przykład pokazuje, że `abstract` jest prawidłowy w kompilacjach kodu natywnego.

### <a name="code"></a>Kod

```cpp
// abstract_native_keyword.cpp
class X abstract {};

int main() {
   X * MyX = new X;   // C3622 cannot instantiate abstract class
}
```

## <a name="see-also"></a>Zobacz także

[Specyfikatory przesłonięć](../extensions/override-specifiers-cpp-component-extensions.md)
