---
title: (atrybut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.module
helpviewer_keywords:
- module attributes
ms.assetid: 02223b2a-62b5-4262-832f-564b1e11e58e
ms.openlocfilehash: 9d4f9e23aaf182e28930ba3a4462b07533ba9015
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754377"
---
# <a name="module-c"></a>moduł (C++)

Definiuje blok biblioteki w pliku .idl.

## <a name="syntax"></a>Składnia

```cpp
[ module (type=dll, name=string, version=1.0, uuid=uuid, lcid=integer, control=boolean, helpstring=string, helpstringdll=string, helpfile=string, helpcontext=integer, helpstringcontext=integer, hidden=boolean, restricted=boolean, custom=string, resource_name=string,) ];
```

### <a name="parameters"></a>Parametry

*Typu*<br/>
(Opcjonalnie) Może być jedną z następujących czynności:

- `dll`Dodaje funkcje i klasy, które umożliwiają wynikową bibliotekę DLL do działania jako serwer COM w toku. Jest to wartość domyślna.

- `exe`Dodaje funkcje i klasy, które umożliwiają wynikowy plik wykonywalny do działania jako serwer COM poza procesem.

- `service`Dodaje funkcje i klasy, które umożliwiają wynikowy plik wykonywalny do działania jako usługa NT.

- `unspecified`Wyłącza wtrysk kodu ATL związane z atrybutem modułu: iniekcja klasy modułu ATL, globalne wystąpienie _AtlModule i funkcje punktu wejścia. Nie wyłącza wtrysku kodu ATL z powodu innych atrybutów w projekcie.

*Nazwa*<br/>
(Opcjonalnie) Nazwa bloku biblioteki.

*Wersja*<br/>
(Opcjonalnie) Numer wersji, który chcesz przypisać do bloku biblioteki. Wartość domyślna to 1.0.

*uuid*<br/>
Unikatowy identyfikator biblioteki. Jeśli ten parametr zostanie pominięty, identyfikator zostanie automatycznie wygenerowany dla biblioteki. Może być konieczne pobranie *uuid* bloku biblioteki, co można zrobić za pomocą **identyfikatora __uuidof(** *nazwa biblioteki* **)**.

*lcid*<br/>
Parametr lokalizacji. Zobacz [lcid](/windows/win32/Midl/lcid) aby uzyskać więcej informacji.

*Kontroli*<br/>
(Opcjonalnie) Określa, że wszystkie współklasy w bibliotece są formantami.

*helpstring*<br/>
Określa bibliotekę typów.

*helpstringdll*<br/>
(Opcjonalnie) Ustawia nazwę pliku dll, który ma być używany do odnośniania ciągu dokumentu. Zobacz [helpstringdll aby](/windows/win32/Midl/helpstringdll) uzyskać więcej informacji.

*helpfile*<br/>
(Opcjonalnie) Nazwa pliku **Pomocy** dla biblioteki typów.

*helpcontext*<br/>
(Opcjonalnie) **Identyfikator Pomocy** dla tej biblioteki typów.

*helpstringcontext*<br/>
(Opcjonalnie) Zobacz [helpstringcontext aby](helpstringcontext.md) uzyskać więcej informacji.

*Ukryte*<br/>
(Opcjonalnie) Zapobiega wyświetlaniu całej biblioteki. To użycie jest przeznaczone do użytku z formantami. Hosty muszą utworzyć nową bibliotekę typów, która otacza formant z właściwościami rozszerzonymi. Zobacz [ukryty](/windows/win32/Midl/hidden) atrybut MIDL, aby uzyskać więcej informacji.

*restricted*<br/>
(Opcjonalnie) Członkowie biblioteki nie mogą być wywoływani arbitralnie. Zobacz [atrybut midl z ograniczeniami,](/windows/win32/Midl/restricted) aby uzyskać więcej informacji.

*Niestandardowe*<br/>
(Opcjonalnie) Jeden lub więcej atrybutów; jest to podobne do atrybutu [niestandardowego.](custom-cpp.md) Pierwszym parametrem do *niestandardowego* jest identyfikator GUID atrybutu. Przykład:

```
[module(custom={guid,1}, custom={guid1,2})]
```

*resource_name*<br/>
Identyfikator zasobu ciągu pliku .rgs używanego do rejestrowania identyfikatora aplikacji biblioteki DLL, pliku wykonywalnego lub usługi. Gdy moduł jest typu usługi, ten argument jest również używany do uzyskania identyfikatora ciągu zawierającego nazwę usługi.

> [!NOTE]
> Zarówno plik rgs, jak i ciąg zawierający nazwę usługi powinny zawierać tę samą wartość liczbową.

## <a name="remarks"></a>Uwagi

Jeśli nie określisz *ograniczonego* [parametru do emitowania,](emitidl.md) **moduł** jest wymagany w każdym programie, który używa atrybutów C++.

Blok biblioteki zostanie utworzony, jeśli oprócz atrybutu **modułu** kod źródłowy używa również [dispinterface,](dispinterface.md) [dual](dual.md), [object](object-cpp.md)lub atrybutu, który implikuje [coclass](coclass.md).

Jeden blok biblioteki jest dozwolony w pliku .idl. Wiele wpisów modułu w kodzie źródłowym zostaną scalone, z najnowszych wartości parametrów zaimplementowanych.

Jeśli ten atrybut jest używany w projekcie, który używa ATL, zmienia się zachowanie atrybutu. Oprócz powyższego zachowania atrybut wstawia również obiekt globalny `_AtlModule`(o nazwie ) poprawnego typu i dodatkowy kod pomocy technicznej. Jeśli atrybut jest autonomiczny, wstawia klasę pochodzącą z poprawnego typu modułu. Jeśli atrybut jest stosowany do klasy, dodaje klasę podstawową poprawnego typu modułu. Prawidłowy typ jest określany przez wartość parametru *typu:*

- `type` = **Dll**

   [CAtlDllModuleT](../../atl/reference/catldllmodulet-class.md) jest używany jako klasa podstawowa i standardowe punkty wejścia biblioteki DLL wymagane dla serwera COM. Te punkty wejścia to [DllMain](/windows/win32/Dlls/dllmain), [DllRegisterServer](/windows/win32/api/olectl/nf-olectl-dllregisterserver), [DllUnRegisterServer](/windows/win32/api/olectl/nf-olectl-dllunregisterserver), [DllCanUnloadNow](/windows/win32/api/combaseapi/nf-combaseapi-dllcanunloadnow)i [DllGetClassObject](/windows/win32/api/combaseapi/nf-combaseapi-dllgetclassobject).

- `type` = **Exe**

   [CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md) jest używany jako klasa podstawowa i standardowy wykonywalny punkt wejścia [WinMain](/windows/win32/api/winbase/nf-winbase-winmain).

- `type` = **Usługi**

   [CAtlServiceModuleT](../../atl/reference/catlservicemodulet-class.md) jest używany jako klasa podstawowa i standardowy wykonywalny punkt wejścia [WinMain](/windows/win32/api/winbase/nf-winbase-winmain).

- `type` = **Nieokreślony**

   Wyłącza wtrysk kodu ATL związane z atrybutem modułu.

## <a name="example"></a>Przykład

Poniższy kod pokazuje, jak utworzyć blok biblioteki w wygenerowanym pliku .idl.

```cpp
// cpp_attr_ref_module1.cpp
// compile with: /LD
[module(name="MyLibrary", version="1.2", helpfile="MyHelpFile")];
```

Poniższy kod pokazuje, że można podać własną implementację funkcji, która pojawi się w kodzie, który został wstrzyknięty w wyniku korzystania z **modułu**. Zobacz [/Fx,](../../build/reference/fx-merge-injected-code.md) aby uzyskać więcej informacji na temat przeglądania wstrzykniętego kodu. Aby zastąpić jedną z funkcji wstawionych przez atrybut **modułu,** należy wykonać klasę, która będzie zawierać implementację funkcji i sprawić, że atrybut **modułu** będzie stosowany do tej klasy.

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
|**Wymagane atrybuty**|Brak|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji, zobacz [Konteksty atrybutów](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz też

[Atrybuty IDL](idl-attributes.md)<br/>
[Atrybuty klasy](class-attributes.md)<br/>
[Atrybuty autonomiczne](stand-alone-attributes.md)<br/>
[Atrybuty Typedef, Enum, Union i Struct](typedef-enum-union-and-struct-attributes.md)<br/>
[usesgetlasterror](usesgetlasterror.md)<br/>
[Biblioteki](/windows/win32/Midl/library)<br/>
[helpcontext](helpcontext.md)<br/>
[helpstring](helpstring.md)<br/>
[helpfile](helpfile.md)<br/>
[Wersja](version-cpp.md)
