---
title: REF new, gcnew (C + +/ CLI i C + +/ CX)
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
ms.openlocfilehash: f3dd0b73e300b44cb4f35e42683725813453d7de
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "59039432"
---
# <a name="ref-new-gcnew--ccli-and-ccx"></a>REF new, gcnew (C + +/ CLI i C + +/ CX)

**Ref nowe** agregacji — słowo kluczowe przydziela wystąpienie typu, który jest bezużyteczne, gdy obiekt staje się niedostępny, a który zwraca uchwyt ([^](handle-to-object-operator-hat-cpp-component-extensions.md)) do przydzielonego obiektu.

## <a name="all-runtimes"></a>Wszystkie środowiska wykonawcze

Pamięć dla wystąpienia typu, który jest przydzielany przez **ref nowe** jest automatyczne cofnięcie przydziału.

A **ref nowe** zgłasza operacji `OutOfMemoryException` przypadku nie można przydzielić pamięci.

Aby uzyskać więcej informacji dotyczących sposobu przydzielone i bez alokacji pamięci dla typów natywnych języka C++, zobacz [nowy i delete — operatory](../cpp/new-and-delete-operators.md).

## <a name="windows-runtime"></a>Środowisko wykonawcze systemu Windows

Użyj **ref nowe** można przydzielić pamięci dla obiektów środowiska wykonawczego Windows, którego okres istnienia, którą chcesz administrować automatycznie. Obiekt jest automatycznie cofniętą alokacją, gdy jego licznik odwołań zbliża się do zera, która następuje po ostatniej kopii odwołanie stała się poza zakresem. Aby uzyskać więcej informacji, zobacz [klasy i struktury odwołania](../cppcx/ref-classes-and-structs-c-cx.md).

### <a name="requirements"></a>Wymagania

— Opcja kompilatora: `/ZW`

## <a name="common-language-runtime"></a>środowiska uruchomieniowe w trakcie wykonania

Pamięć dla typu zarządzanego (odwołania lub typu wartości) została przydzielona przez **gcnew**i za pomocą wyrzucania elementów bezużytecznych z cofniętą alokacją.

### <a name="requirements"></a>Wymagania

— Opcja kompilatora: `/clr`

### <a name="examples"></a>Przykłady

W poniższym przykładzie użyto **gcnew** przydzielić obiektu wiadomości.

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

W poniższym przykładzie użyto **gcnew** utworzyć opakowanym typem wartościowym do użycia, takich jak typ odwołania.

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

## <a name="see-also"></a>Zobacz także

[Component Extensions dla platformy .NET i platformy uniwersalnej systemu Windows](component-extensions-for-runtime-platforms.md)