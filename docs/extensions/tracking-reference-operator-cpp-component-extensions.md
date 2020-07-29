---
title: Operator odwołania śledzenia (C++/CLI i C++/CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- '%'
helpviewer_keywords:
- tracking references
- '% tracking reference [C++]'
ms.assetid: 142a7269-ab69-4b54-a6d7-833bef06228f
ms.openlocfilehash: 93f56580f35ffc1f6e517905467c3deb92922f5f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218016"
---
# <a name="tracking-reference-operator-ccli-and-ccx"></a>Operator odwołania śledzenia (C++/CLI i C++/CX)

*Odwołanie śledzące* ( `%` ) zachowuje się jak zwykłe odwołanie C++ ( `&` ), z tym że gdy obiekt jest przypisany do odwołania śledzącego, licznik odwołań obiektu jest zwiększany.

## <a name="all-platforms"></a>Wszystkie platformy

Odwołanie śledzące ma następujące cechy.

- Przypisanie obiektu do odwołania śledzenia powoduje zwiększenie liczby odwołań obiektu.

- Odwołanie natywne ( `&` ) jest wynikiem, gdy użytkownik odwołuje się do `*` . Odwołanie śledzące ( `%` ) to wynik, gdy należy usunąć odwołanie do `^` . O ile masz `%` do obiektu, obiekt pozostanie aktywny w pamięci.

- `.`Operator dostępu do elementów członkowskich kropka () służy do uzyskiwania dostępu do elementu członkowskiego obiektu.

- Odwołania śledzenia są prawidłowe dla typów wartości i uchwytów (na przykład `String^` ).

- Odwołanie do śledzenia nie może mieć przypisanej wartości null lub **`nullptr`** Value. Odwołanie śledzące może zostać ponownie przypisane do innego prawidłowego obiektu tyle razy, ile jest to wymagane.

- Nie można użyć odwołania śledzącego jako operatora jednoargumentowego Take-Address.

## <a name="windows-runtime"></a>Środowisko wykonawcze systemu Windows

Odwołanie śledzenia zachowuje się jak standardowe odwołanie języka C++, z tą różnicą, że procent jest liczony jako odwołanie. Poniższy fragment kodu przedstawia sposób konwersji między typami% i ^:

```cpp
Foo^ spFoo = ref new Foo();
Foo% srFoo = *spFoo;
Foo^ spFoo2 = %srFoo;
```

Poniższy przykład pokazuje, jak przekazać ^ do funkcji, która pobiera%.

```cpp
ref class Foo sealed {};

    // internal or private
    void UseFooHelper(Foo% f)
    {
        auto x = %f;
    }

    // public method on ABI boundary
    void UseFoo(Foo^ f)
    {
        if (f != nullptr) { UseFooHelper(*f); }
    }
```

## <a name="common-language-runtime"></a>środowiska uruchomieniowe w trakcie wykonania

W języku C++/CLI można użyć odwołania śledzenia do dojścia w przypadku powiązania z obiektem typu CLR na stertie zebranych elementów bezużytecznych.

W środowisku CLR wartość zmiennej odwołania śledzenia jest aktualizowana automatycznie za każdym razem, gdy moduł zbierający elementy bezużyteczne przeniesie obiekt, do którego się odwołuje.

Odwołanie śledzące można zadeklarować tylko na stosie. Odwołanie śledzące nie może być składową klasy.

Nie jest możliwe posiadanie natywnego odwołania C++ do obiektu na stosie zebranych elementów bezużytecznych.

Aby uzyskać więcej informacji na temat śledzenia odwołań w języku C++/CLI, zobacz:

- [Instrukcje: korzystanie z odwołań śledzenia w języku C++/CLI](../dotnet/how-to-use-tracking-references-in-cpp-cli.md)

### <a name="examples"></a>Przykłady

Poniższy przykład dla języka C++/CLI pokazuje, jak używać odwołania śledzącego z typami natywnymi i zarządzanymi.

```cpp
// tracking_reference_1.cpp
// compile with: /clr
ref class MyClass {
public:
   int i;
};

value struct MyStruct {
   int k;
};

int main() {
   MyClass ^ x = ref new MyClass;
   MyClass ^% y = x;   // tracking reference handle to reference object

   int %ti = x->i;   // tracking reference to member of reference type

   int j = 0;
   int %tj = j;   // tracking reference to object on the stack

   int * pi = new int[2];
   int % ti2 = pi[0];   // tracking reference to object on native heap

   int *% tpi = pi;   // tracking reference to native pointer

   MyStruct ^ x2 = ref new MyStruct;
   MyStruct ^% y2 = x2;   // tracking reference to value object

   MyStruct z;
   int %tk = z.k;   // tracking reference to member of value type

   delete[] pi;
}
```

Poniższy przykład dla języka C++/CLI pokazuje, jak powiązać odwołanie śledzące z tablicą.

```cpp
// tracking_reference_2.cpp
// compile with: /clr
using namespace System;

int main() {
   array<int> ^ a = ref new array<Int32>(5);
   a[0] = 21;
   Console::WriteLine(a[0]);
   array<int> ^% arr = a;
   arr[0] = 222;
   Console::WriteLine(a[0]);
}
```

```Output
21
222
```
