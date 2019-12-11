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
ms.openlocfilehash: 11dbc196a89a224afe02312fbe4dff99d8467f4c
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988247"
---
# <a name="how-to-declare-handles-in-native-types"></a>Porady: deklarowanie dojść w typach natywnych

Nie można zadeklarować typu dojścia w typie natywnym. Vcclr. h udostępnia szablon otoki bezpiecznego typu `gcroot`, aby odwołać się do obiektu CLR ze C++ sterty. Ten szablon umożliwia osadzenie dojścia wirtualnego w typie natywnym i traktuje go tak, jakby był typem podstawowym. W większości przypadków można użyć obiektu `gcroot` jako typu osadzonego bez rzutowania. Jednak [w przypadku każdego programu w programie](../dotnet/for-each-in.md)należy użyć `static_cast`, aby pobrać bazowe odwołanie zarządzane.

Szablon `gcroot` jest implementowany przy użyciu obiektów klasy wartości system:: Runtime:: InteropServices:: GCHandle, która zapewnia "uchwyty" w stercie zebranych elementów bezużytecznych. Należy zauważyć, że same uchwyty nie są zbierane jako elementy bezużyteczne i są zwalniane, gdy nie są już używane przez destruktor w klasie `gcroot` (tego destruktora nie można wywołać ręcznie). Jeśli utworzysz wystąpienie obiektu `gcroot` na stercie natywnym, musisz wywołać metodę Delete dla tego zasobu.

Środowisko uruchomieniowe będzie zachować skojarzenie między uchwytem a obiektem CLR, do którego się odwołuje. Gdy obiekt CLR jest przenoszony z sterty zebranych elementów bezużytecznych, uchwyt zwróci nowy adres obiektu. Zmienna nie musi być przypięta, zanim zostanie przypisana do szablonu `gcroot`.

## <a name="example"></a>Przykład

Ten przykład pokazuje, jak utworzyć obiekt `gcroot` na stosie natywnym.

```cpp
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

Ten przykład pokazuje, jak utworzyć obiekt `gcroot` na stercie natywnym.

```cpp
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

Ten przykład pokazuje, jak używać `gcroot` do przechowywania odwołań do typów wartości (nie typów odwołań) w typie natywnym przy użyciu `gcroot` w typie opakowanym.

```cpp
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

## <a name="see-also"></a>Zobacz także

[Korzystanie z międzyoperacyjności języka C++ (niejawna funkcja PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)
