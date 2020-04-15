---
title: 'Jak: Declare Override Specifiers (C++/CLI)'
ms.date: 11/04/2016
helpviewer_keywords:
- override specifiers in native compilation, overriding
ms.assetid: d0551836-9ac7-41eb-a6e9-a4b3ef60767d
ms.openlocfilehash: 9f3f6855f257d0af250b9bbdd2c0360b308ce775
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374447"
---
# <a name="how-to-declare-override-specifiers-in-native-compilations-ccli"></a>Porady: deklarowanie specyfikatorów przesłonięć w kompilacjach kodu natywnego (C++/CLI)

[zapieczętowane,](../extensions/sealed-cpp-component-extensions.md) [abstrakcyjne](../extensions/abstract-cpp-component-extensions.md)i [zastępowane](../extensions/override-cpp-component-extensions.md) są dostępne w kompilacjach, które nie używają **/ZW** lub [/clr](../build/reference/clr-common-language-runtime-compilation.md).

> [!NOTE]
> Język standardowy ISO C++11 ma identyfikator [zastępowania](../cpp/override-specifier.md) i [ostateczny](../cpp/final-specifier.md) identyfikator, a oba `final` są `sealed` obsługiwane w programie Visual Studio Use zamiast w kodzie, który ma być skompilowany jako tylko natywny.

## <a name="example"></a>Przykład

### <a name="description"></a>Opis

Poniższy przykład `sealed` pokazuje, że jest prawidłowy w kompilacjach natywnych.

### <a name="code"></a>Code

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

### <a name="code"></a>Code

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

W tym `abstract` przykładzie pokazano, że jest prawidłowy w kompilacjach natywnych.

### <a name="code"></a>Code

```cpp
// abstract_native_keyword.cpp
class X abstract {};

int main() {
   X * MyX = new X;   // C3622 cannot instantiate abstract class
}
```

## <a name="see-also"></a>Zobacz też

[Specyfikatory zastąpienia](../extensions/override-specifiers-cpp-component-extensions.md)
