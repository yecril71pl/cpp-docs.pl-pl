---
title: 'Porady: definiowanie statycznego konstruktora interfejsu (C++/CLI)'
ms.date: 11/04/2016
helpviewer_keywords:
- constructors [C++]
- static constructors, interface
- interface static constructor
ms.assetid: 1f031cb2-e94f-43dc-819b-44cf2faaaa49
ms.openlocfilehash: 562605a579ac372e4a69953853a6e32668357565
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988239"
---
# <a name="how-to-define-an-interface-static-constructor-ccli"></a>Porady: definiowanie statycznego konstruktora interfejsu (C++/CLI)

Interfejs może mieć Konstruktor statyczny, który może służyć do inicjowania statycznych elementów członkowskich danych.  Konstruktor statyczny zostanie wywołany najwyżej raz i zostanie wywołany przed pierwszym uzyskaniem dostępu do statycznego elementu członkowskiego.

## <a name="example"></a>Przykład

```cpp
// mcppv2_interface_class2.cpp
// compile with: /clr
using namespace System;

interface struct MyInterface {
   static int i;
   static void Test() {
      Console::WriteLine(i);
   }

   static MyInterface() {
      Console::WriteLine("in MyInterface static constructor");
      i = 99;
   }
};

ref class MyClass : public MyInterface {};

int main() {
   MyInterface::Test();
   MyClass::MyInterface::Test();

   MyInterface ^ mi = gcnew MyClass;
   mi->Test();
}
```

```Output
in MyInterface static constructor
99
99
99
```

## <a name="see-also"></a>Zobacz także

[interface class](../extensions/interface-class-cpp-component-extensions.md)
