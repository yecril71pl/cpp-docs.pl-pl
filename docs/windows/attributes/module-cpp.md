---
title: module (C++ atrybut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.module
helpviewer_keywords:
- module attributes
ms.assetid: 02223b2a-62b5-4262-832f-564b1e11e58e
ms.openlocfilehash: e93073a1728063038ddd4e28dbb313854ee3c8c5
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80166695"
---
# <a name="module-c"></a>moduł (C++)

Definiuje blok biblioteki w pliku IDL.

## <a name="syntax"></a>Składnia

```cpp
[ module (type=dll, name=string, version=1.0, uuid=uuid, lcid=integer, control=boolean, helpstring=string, helpstringdll=string, helpfile=string, helpcontext=integer, helpstringcontext=integer, hidden=boolean, restricted=boolean, custom=string, resource_name=string,) ];
```

### <a name="parameters"></a>Parametry

*type*<br/>
Obowiązkowe Może być jedną z następujących czynności:

- `dll` dodaje funkcje i klasy, które umożliwiają działanie biblioteki DLL w procesie jako serwer COM. Jest to wartość domyślna.

- `exe` dodaje funkcje i klasy, które umożliwiają działanie programu wykonywalnego jako poza procesem.

- `service` dodaje funkcje i klasy, które umożliwiają działanie programu wykonywalnego jako usługi NT.

- `unspecified` wyłącza iniekcję kodu ATL związanego z atrybutem modułu: iniekcja klasy modułu ATL, globalnych _AtlModule wystąpień i funkcji punktu wejścia. Nie wyłącza iniekcji kodu ATL ze względu na inne atrybuty projektu.

*Nazwij*<br/>
Obowiązkowe Nazwa bloku biblioteki.

*version*<br/>
Obowiązkowe Numer wersji, który ma zostać przypisany do bloku biblioteki. Wartość domyślna to 1,0.

*uuid*<br/>
Unikatowy identyfikator biblioteki. Jeśli pominięto ten parametr, identyfikator zostanie automatycznie wygenerowany dla biblioteki. Może być konieczne pobranie *identyfikatora UUID* bloku biblioteki, który można wykonać przy użyciu identyfikatora **__uuidof (** *LibraryName* **)** .

*lcid*<br/>
Parametr lokalizacji. Aby uzyskać więcej informacji, zobacz [LCID](/windows/win32/Midl/lcid) .

*control*<br/>
Obowiązkowe Określa, że wszystkie klasy coclass w bibliotece są kontrolkami.

*helpstring*<br/>
Określa bibliotekę typów.

*helpstringdll*<br/>
Obowiązkowe Ustawia nazwę pliku dll, który ma być używany do wykonywania wyszukiwania ciągu dokumentu. Aby uzyskać więcej informacji, zobacz [helpstringdll](/windows/win32/Midl/helpstringdll) .

*helpfile*<br/>
Obowiązkowe Nazwa pliku **pomocy** dla biblioteki typów.

*helpcontext*<br/>
Obowiązkowe **Identyfikator pomocy** dla tej biblioteki typów.

*helpstringcontext*<br/>
Obowiązkowe Aby uzyskać więcej informacji, zobacz [helpstringcontext](helpstringcontext.md) .

*hidden*<br/>
Obowiązkowe Zapobiega wyświetlaniu całej biblioteki. To użycie jest przeznaczone do użycia z kontrolkami. Hosty muszą utworzyć nową bibliotekę typów, która zawija formant z rozszerzonymi właściwościami. Aby uzyskać więcej informacji, zobacz [ukryty](/windows/win32/Midl/hidden) atrybut MIDL.

*restricted*<br/>
Obowiązkowe Elementy członkowskie biblioteki nie mogą być wywoływane arbitralnie. Aby uzyskać więcej informacji, zobacz atrybut MIDL z [ograniczeniami](/windows/win32/Midl/restricted) .

*custom*<br/>
Obowiązkowe Jeden lub więcej atrybutów; jest to podobne do atrybutu [niestandardowego](custom-cpp.md) . Pierwszy parametr do *niestandardowego* jest identyfikatorem GUID atrybutu. Na przykład:

```
[module(custom={guid,1}, custom={guid1,2})]
```

*resource_name*<br/>
Identyfikator zasobu ciągu pliku. RGS używany do rejestrowania identyfikatora aplikacji DLL, wykonywalnego lub usługi. Gdy moduł jest typu usługa, ten argument jest również używany do uzyskania identyfikatora ciągu zawierającego nazwę usługi.

> [!NOTE]
> Zarówno plik. RGS, jak i ciąg zawierający nazwę usługi powinny zawierać tę samą wartość liczbową.

## <a name="remarks"></a>Uwagi

Jeśli nie określisz parametru z *ograniczeniami* [emitidl](emitidl.md), **moduł** jest wymagany w dowolnym programie, C++ który używa atrybutów.

Blok biblioteki zostanie utworzony, jeśli oprócz atrybutu **module** kod źródłowy korzysta również z [dispinterface](dispinterface.md), [podwójnego](dual.md) [obiektu](object-cpp.md)lub atrybutu, który implikuje [klasę coclass](coclass.md).

Jeden blok biblioteki jest dozwolony w pliku IDL. Wiele wpisów modułu w kodzie źródłowym zostanie scalonych z najnowszymi wartościami parametrów, które są implementowane.

Jeśli ten atrybut jest używany w projekcie, który korzysta z ATL, zachowanie zmiany atrybutu. Oprócz powyższego zachowania, atrybut wstawia również obiekt globalny (o nazwie `_AtlModule`) poprawnego typu i dodatkowy kod pomocniczy. Jeśli atrybut jest autonomiczny, wstawia klasę pochodną poprawnego typu modułu. Jeśli atrybut jest stosowany do klasy, dodaje klasę bazową poprawnego typu modułu. Prawidłowy typ jest określany przez wartość parametru *typu* :

- `type` = **dll**

   [CAtlDllModuleT](../../atl/reference/catldllmodulet-class.md) jest używany jako klasa bazowa i standardowe punkty wejścia biblioteki DLL wymagane dla serwera com. Te punkty wejścia to [DllMain](/windows/win32/Dlls/dllmain), [DllRegisterServer](/windows/win32/api/olectl/nf-olectl-dllregisterserver), [DllUnregisterServer](/windows/win32/api/olectl/nf-olectl-dllunregisterserver), [DllCanUnloadNow](/windows/win32/api/combaseapi/nf-combaseapi-dllcanunloadnow)i [DllGetClassObject](/previous-versions//dd797891\(v=vs.85\)).

- `type` = **exe**

   [CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md) jest używany jako klasa bazowa i standardowy punkt wejścia [WinMain](/windows/win32/api/winbase/nf-winbase-winmain).

- **usługa**  = `type`

   [Funkcja CAtlServiceModuleT](../../atl/reference/catlservicemodulet-class.md) jest używany jako klasa bazowa i standardowy punkt wejścia [WinMain](/windows/win32/api/winbase/nf-winbase-winmain).

- nieokreślony **unspecified** `type` = 

   Wyłącza iniekcję kodu ATL związanego z atrybutem modułu.

## <a name="example"></a>Przykład

Poniższy kod pokazuje, jak utworzyć blok biblioteki w wygenerowanym pliku IDL.

```cpp
// cpp_attr_ref_module1.cpp
// compile with: /LD
[module(name="MyLibrary", version="1.2", helpfile="MyHelpFile")];
```

Poniższy kod pokazuje, że można podać własną implementację funkcji, która będzie widoczna w kodzie, który został wstrzykiwany w wyniku użycia **modułu**. Zobacz [/FX](../../build/reference/fx-merge-injected-code.md) , aby uzyskać więcej informacji na temat wyświetlania iniekcji kodu. Aby przesłonić jedną z funkcji wstawianych przez atrybut **modułu** , należy utworzyć klasę, która będzie zawierać implementację funkcji, i nadać **jej atrybut do tej klasy** .

```cpp
// cpp_attr_ref_module2.cpp
// compile with: /LD /link /OPT:NOREF
#include <atlbase.h>
#include <atlcom.h>
#include <atlwin.h>
#include <atltypes.h>
#include <atlctl.h>
#include <atlhost.h>
#include <atlplus.h>

// no semicolon after attribute block
[module(dll, name="MyLibrary", version="1.2", helpfile="MyHelpFile")]
// module attribute now applies to this class
class CMyClass {
public:
BOOL WINAPI DllMain(DWORD dwReason, LPVOID lpReserved) {
   // add your own code here
   return __super::DllMain(dwReason, lpReserved);
   }
};
```

## <a name="requirements"></a>Wymagania

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|Dowolnym miejscu|
|**Powtarzalne**|Nie|
|**Wymagane atrybuty**|None|
|**Nieprawidłowe atrybuty**|None|

Aby uzyskać więcej informacji, zobacz [konteksty atrybutów](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz też

[Atrybuty IDL](idl-attributes.md)<br/>
[Atrybuty klasy](class-attributes.md)<br/>
[Oddzielne atrybuty](stand-alone-attributes.md)<br/>
[Atrybuty Typedef, Enum, Union oraz Struct](typedef-enum-union-and-struct-attributes.md)<br/>
[usesgetlasterror](usesgetlasterror.md)<br/>
[biblioteki](/windows/win32/Midl/library)<br/>
[helpcontext](helpcontext.md)<br/>
[helpstring](helpstring.md)<br/>
[helpfile](helpfile.md)<br/>
[version](version-cpp.md)
