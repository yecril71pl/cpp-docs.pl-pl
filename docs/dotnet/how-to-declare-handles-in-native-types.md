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
ms.openlocfilehash: deba9804b9c5c278b3ffcef2923bc8f89fefa676
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/16/2020
ms.locfileid: "90684537"
---
# <a name="how-to-declare-handles-in-native-types"></a>Porady: deklarowanie dojść w typach natywnych

Nie można zadeklarować typu dojścia w typie natywnym. Vcclr. h udostępnia szablon otoki bezpiecznego typu, `gcroot` Aby odwołać się do obiektu CLR ze sterty języka C++. Ten szablon umożliwia osadzenie dojścia wirtualnego w typie natywnym i traktuje go tak, jakby był typem podstawowym. W większości przypadków można użyć `gcroot` obiektu jako typu osadzonego bez rzutowania. Jednak [w przypadku każdego z nich](../dotnet/for-each-in.md)należy użyć, **`static_cast`** Aby pobrać bazowe odwołanie zarządzane.

`gcroot`Szablon jest implementowany przy użyciu obiektów klasy wartości system:: Runtime:: InteropServices:: GCHandle, który zapewnia "Handles" na stosie zebranych elementów bezużytecznych. Należy zauważyć, że same uchwyty nie są odbierane jako elementy bezużyteczne i są zwalniane, gdy nie są już używane przez destruktor w `gcroot` klasie (tego destruktora nie można wywołać ręcznie). Jeśli tworzysz wystąpienie `gcroot` obiektu na stercie natywnym, musisz wywołać metodę Delete dla tego zasobu.

Środowisko uruchomieniowe będzie zachować skojarzenie między uchwytem a obiektem CLR, do którego się odwołuje. Gdy obiekt CLR jest przenoszony z sterty zebranych elementów bezużytecznych, uchwyt zwróci nowy adres obiektu. Zmienna nie musi być przypięta, zanim zostanie przypisana do `gcroot` szablonu.

## <a name="examples"></a>Przykłady

Ten przykład pokazuje, jak utworzyć `gcroot` obiekt na stosie natywnym.

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

Ten przykład pokazuje, jak utworzyć `gcroot` obiekt na stercie natywnym.

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

Ten przykład pokazuje, jak używać `gcroot` do przechowywania odwołań do typów wartości (nie typów referencyjnych) w typie natywnym przy użyciu `gcroot` typu opakowanego.

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

[Korzystanie z międzyoperacyjności języka C++ (niejawne PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)
