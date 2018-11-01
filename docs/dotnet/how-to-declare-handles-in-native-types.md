---
title: 'Porady: deklarowanie dojść w typach natywnych'
ms.custom: get-started-article
ms.date: 11/04/2016
f1_keywords:
- gcroot
helpviewer_keywords:
- handles, declaring
- gcroot keyword [C++]
- types [C++], declaring handles in
ms.assetid: b8c0eead-17e5-4003-b21f-b673f997d79f
ms.openlocfilehash: 4b5cd212589be04f5f9f3a5dd6d4496a8f5add2c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50464929"
---
# <a name="how-to-declare-handles-in-native-types"></a>Porady: deklarowanie dojść w typach natywnych

Nie można zadeklarować na typ dojścia w typie natywnym. vcclr.h oferuje szablon bezpieczny otoki `gcroot` do odwoływania się do obiektu CLR ze stosu C++. Ten szablon umożliwia osadzania wirtualnego dojście w typie natywnym i traktować je tak, jakby był to typ podstawowy. W większości przypadków można użyć `gcroot` obiektu jako osadzonego typu, bez żadnych rzutowania. Jednak w przypadku [dla poszczególnych usług, w](../dotnet/for-each-in.md), trzeba użyć `static_cast` do pobrania podstawowego odwołania zarządzane.

`gcroot` Szablonu jest implementowany przy użyciu funkcji klasy wartości System::Runtime::InteropServices::GCHandle, co zapewnia "obsługuje" na stercie zebranych elementów bezużytecznych. Należy pamiętać, że uchwyty sami nie są bezużyteczne i są zwalniane, gdy nie jest już w użyciu przez destruktora w `gcroot` klasy (ten destruktor nie można wywołać ręcznie). W przypadku tworzenia wystąpienia `gcroot` obiektu na natywnej stercie, należy wywołać usuwanie na taki zasób.

Środowisko uruchomieniowe zachowają skojarzenie między obiektu CLR, który odwołuje się do uchwytu. Gdy przenosi obiekt CLR za pomocą stosu odśmieconej pamięci, uchwyt zwróci nowy adres obiektu. Zmienna nie będzie musiał przypięty, zanim zostanie on przypisany do `gcroot` szablonu.

## <a name="example"></a>Przykład

W tym przykładzie przedstawiono sposób tworzenia `gcroot` obiektów na stosie natywnych.

```
// mcpp_gcroot.cpp
// compile with: /clr
#include <vcclr.h>
using namespace System;

class CppClass {
public:
   gcroot<String^> str;   // can use str as if it were String^
   CppClass() {}
};

int main() {
   CppClass c;
   c.str = gcnew String("hello");
   Console::WriteLine( c.str );   // no cast required
}
```

```Output
hello
```

## <a name="example"></a>Przykład

W tym przykładzie przedstawiono sposób tworzenia `gcroot` obiekt sterty natywnej.

```
// mcpp_gcroot_2.cpp
// compile with: /clr
// compile with: /clr
#include <vcclr.h>
using namespace System;

struct CppClass {
   gcroot<String ^> * str;
   CppClass() : str(new gcroot<String ^>) {}

   ~CppClass() { delete str; }

};

int main() {
   CppClass c;
   *c.str = gcnew String("hello");
   Console::WriteLine( *c.str );
}
```

```Output
hello
```

## <a name="example"></a>Przykład

Ten przykład ilustruje sposób używania `gcroot` do przechowywania odwołań do typów wartości (nie typy referencyjne) w polu typu natywnego za pomocą `gcroot` na typ spakowany.

```
// mcpp_gcroot_3.cpp
// compile with: /clr
#include < vcclr.h >
using namespace System;

public value struct V {
   String^ str;
};

class Native {
public:
   gcroot< V^ > v_handle;
};

int main() {
   Native native;
   V v;
   native.v_handle = v;
   native.v_handle->str = "Hello";
   Console::WriteLine("String in V: {0}", native.v_handle->str);
}
```

```Output
String in V: Hello
```

## <a name="see-also"></a>Zobacz też

[Korzystanie z międzyoperacyjności języka C++ (niejawna funkcja PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)