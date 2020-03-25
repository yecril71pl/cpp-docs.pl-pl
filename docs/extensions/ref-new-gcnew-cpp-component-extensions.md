---
title: ref new, gcnew (C++/CLI i C++/CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- gcnew
- ref new
- gcnew_cpp
helpviewer_keywords:
- ref new keyword (C++)
- gcnew keyword [C++]
ms.assetid: 388a62da-c2df-4a94-a9a2-205b53e577da
ms.openlocfilehash: f7269a62d7899df4eb89f6dd9487310c0fda0b4d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80181814"
---
# <a name="ref-new-gcnew--ccli-and-ccx"></a>ref new, gcnew (C++/CLI i C++/CX)

Słowo kluczowe **ref new** Aggregate przydziela wystąpienie typu, który jest wyrzucany przez elementy bezużyteczne, gdy obiekt stał się niedostępny, i zwraca dojście ([^](handle-to-object-operator-hat-cpp-component-extensions.md)) do przydzielonego obiektu.

## <a name="all-runtimes"></a>Wszystkie środowiska wykonawcze

Przydział pamięci dla wystąpienia typu, który jest przydzielony przez **ref new** , zostaje cofnięty automatycznie.

**Nowa** operacja zgłasza `OutOfMemoryException`, jeśli nie może przydzielić pamięci.

Aby uzyskać więcej informacji o sposobie przydzielenia i cofania przydziału pamięci dla typów natywnych C++ , zobacz [Operatory New i DELETE](../cpp/new-and-delete-operators.md).

## <a name="windows-runtime"></a>Środowisko wykonawcze systemu Windows

Użyj **ref new** , aby przydzielić pamięć dla środowisko wykonawcze systemu Windows obiektów, których okres istnienia ma być zarządzany automatycznie. Obiekt zostanie automatycznie cofnięty, gdy jego liczba odwołań spadnie do zera, co występuje po zakończeniu ostatniej kopii odwołania poza zakresem. Aby uzyskać więcej informacji, zobacz [klasy referencyjne i struktury](../cppcx/ref-classes-and-structs-c-cx.md).

### <a name="requirements"></a>Wymagania

Opcja kompilatora: `/ZW`

## <a name="common-language-runtime"></a>środowiska uruchomieniowe w trakcie wykonania

Pamięć dla typu zarządzanego (odwołanie lub typ wartości) jest przydzielone przez **gcnew**i cofane przy użyciu wyrzucania elementów bezużytecznych.

### <a name="requirements"></a>Wymagania

Opcja kompilatora: `/clr`

### <a name="examples"></a>Przykłady

Poniższy przykład używa **gcnew** do przydzielenia obiektu komunikatu.

```cpp
// mcppv2_gcnew_1.cpp
// compile with: /clr
ref struct Message {
   System::String^ sender;
   System::String^ receiver;
   System::String^ data;
};

int main() {
   Message^ h_Message  = gcnew Message;
  //...
}
```

W poniższym przykładzie użyto **gcnew** , aby utworzyć opakowany typ wartości do użycia jak typ referencyjny.

```cpp
// example2.cpp : main project file.
// compile with /clr
using namespace System;
value class Boxed {
    public:
        int i;
};
int main()
{
    Boxed^ y = gcnew Boxed;
    y->i = 32;
    Console::WriteLine(y->i);
    return 0;
}
```

```Output
32
```

## <a name="see-also"></a>Zobacz też

[Rozszerzenia składników dla platformy .NET i platformy uniwersalnej systemu Windows](component-extensions-for-runtime-platforms.md)
