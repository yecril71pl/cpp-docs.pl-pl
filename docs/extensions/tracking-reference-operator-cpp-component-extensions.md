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
ms.openlocfilehash: ccd31b3e334dc5a4cd2e48b94c9dbe85cf13c16b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368238"
---
# <a name="tracking-reference-operator-ccli-and-ccx"></a>Operator odwołania śledzenia (C++/CLI i C++/CX)

*Odwołanie do* `%`śledzenia ( ) zachowuje się jak`&`zwykłe odwołanie C++ ( ), z tą różnicą, że gdy obiekt jest przypisany do odwołania śledzenia, liczba odwołań do obiektu jest zwiększana.

## <a name="all-platforms"></a>Wszystkie platformy

Odwołanie do śledzenia ma następujące cechy.

- Przypisanie obiektu do odwołania śledzenia powoduje, że liczba odwołań do obiektu ma być zwiększana.

- Odwołanie natywne (`&`) jest wynikiem `*`podczas wyłuskinia . Odwołanie do`%`śledzenia ( ) jest wynikiem `^`wyłuskiwki . Tak długo, jak `%` masz do obiektu, obiekt pozostanie przy życiu w pamięci.

- Operator dostępu`.`do elementu członkowskiego dot ( ) jest używany do uzyskiwania dostępu do elementu członkowskiego obiektu.

- Odwołania do śledzenia są prawidłowe dla typów `String^`wartości i uchwytów (na przykład).

- Odwołanie śledzenia nie można przypisać wartości null lub **nullptr.** Odwołanie do śledzenia może zostać ponownie przypisane do innego prawidłowego obiektu tyle razy, ile jest wymagane.

- Odwołanie śledzenia nie może służyć jako operator dwuwybierającego adresu.

## <a name="windows-runtime"></a>Środowisko wykonawcze systemu Windows

Odwołanie śledzenia zachowuje się jak standardowe odwołanie C++, z tą różnicą, że % jest zliczane przez odwołanie. Poniższy fragment kodu pokazuje, jak konwertować między typami % i ^:

```cpp
Foo^ spFoo = ref new Foo();
Foo% srFoo = *spFoo;
Foo^ spFoo2 = %srFoo;
```

W poniższym przykładzie pokazano, jak przekazać ^ do funkcji, która przyjmuje %.

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

W języku C++/CLI można użyć odwołania śledzenia do dojścia podczas powiązania z obiektem typu CLR na stercie zebranej przez śmieci.

W programie CLR wartość zmiennej referencyjnej śledzenia jest aktualizowana automatycznie za każdym razem, gdy moduł zbierający elementy bezużyteczne przenosi obiekt, do którego istnieje odwołanie.

Odwołanie śledzenia można zadeklarować tylko na stosie. Odwołanie śledzenia nie może być członkiem klasy.

Nie jest możliwe, aby mieć natywne odwołanie C++ do obiektu na stercie zebrane przez śmieci.

Aby uzyskać więcej informacji na temat śledzenia odwołań w języku C++/CLI, zobacz:

- [Instrukcje: korzystanie z odwołań śledzenia w języku C++/interfejsie wiersza polecenia](../dotnet/how-to-use-tracking-references-in-cpp-cli.md)

### <a name="examples"></a>Przykłady

Poniższy przykład dla języka C++/CLI pokazuje, jak używać odwołania śledzenia z typami macierzystymi i zarządzanymi.

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

Poniższy przykład dla języka C++/CLI pokazuje, jak powiązać odwołanie śledzenia do tablicy.

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
