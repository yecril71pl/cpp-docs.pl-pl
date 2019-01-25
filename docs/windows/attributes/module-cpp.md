---
title: Moduł (atrybut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.module
helpviewer_keywords:
- module attributes
ms.assetid: 02223b2a-62b5-4262-832f-564b1e11e58e
ms.openlocfilehash: bafdb65f255ddf33964d22e5ea80a62446c2ad45
ms.sourcegitcommit: c85c8a1226d8fbbaa29f4691ed719f8e6cc6575c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54893525"
---
# <a name="module-c"></a>moduł (C++)

Określa blok biblioteki w pliku .idl.

## <a name="syntax"></a>Składnia

```cpp
[ module (type=dll, name=string, version=1.0, uuid=uuid, lcid=integer, control=boolean, helpstring=string, helpstringdll=string, helpfile=string, helpcontext=integer, helpstringcontext=integer, hidden=boolean, restricted=boolean, custom=string, resource_name=string,) ];
```

### <a name="parameters"></a>Parametry

*type*<br/>
(Opcjonalnie) Może być jedną z następujących czynności:

- `dll` Dodaje funkcje i klasy, które umożliwiają wynikowy DLL do działania jako serwer COM w procesie. Jest to wartość domyślna.

- `exe` Dodaje funkcje i klasy, które pozwalają wynikowy pliku wykonywalnego, aby działały jak poza serwer COM przetwarzania.

- `service` Dodaje funkcje i klasy, które pozwalają wynikowy pliku wykonywalnego do działania jako usługa NT.

- `unspecified` Wyłącza iniekcji kodu biblioteki ATL, powiązany z atrybutem modułu: iniekcji modułu ATL klas, _AtlModule globalnego wystąpienia i wpis punktu funkcji. Nie wyłącza iniekcji kodu biblioteki ATL z powodu innych atrybutów w projekcie.

*Nazwa*<br/>
(Opcjonalnie) Nazwa bloku biblioteki.

*version*<br/>
(Opcjonalnie) Numer wersji, którą chcesz przypisać do bloku biblioteki. Wartość domyślna to 1.0.

*uuid*<br/>
Unikatowy identyfikator dla biblioteki. Jeżeli pominięto ten parametr zostanie automatycznie wygenerowany identyfikator biblioteki. Musisz pobrać *uuid* bloku Biblioteka można wykonać przy użyciu identyfikatora **__uuidof (** *libraryname* **)**.

*lcid*<br/>
Parametr lokalizacji. Zobacz [lcid](/windows/desktop/Midl/lcid) Aby uzyskać więcej informacji.

*control*<br/>
(Opcjonalnie) Określa, że wszystkie klasy coclass w bibliotece kontrolek.

*helpstring*<br/>
Określa plik biblioteki typów.

*helpstringdll*<br/>
(Opcjonalnie) Określa nazwę pliku .dll, aby wykonać wyszukiwanie ciągu dokumentu. Zobacz [helpstringdll —](/windows/desktop/Midl/helpstringdll) Aby uzyskać więcej informacji.

*helpfile*<br/>
(Opcjonalnie) Nazwa **pomocy** pliku biblioteki typów.

*helpcontext*<br/>
(Opcjonalnie) **Identyfikator pomocy** dla tego typu biblioteki.

*helpstringcontext*<br/>
(Opcjonalnie) Zobacz [helpstringcontext —](helpstringcontext.md) Aby uzyskać więcej informacji.

*hidden*<br/>
(Opcjonalnie) Uniemożliwia wyświetlanie całej biblioteki. To obciążenie jest przeznaczony do użytku z formantami. Hosty muszą Utwórz nową bibliotekę typu, który opakowuje formant z rozszerzonych właściwości. Zobacz [ukryte](/windows/desktop/Midl/hidden) atrybutu MIDL, aby uzyskać więcej informacji.

*restricted*<br/>
(Opcjonalnie) Elementy członkowskie biblioteki nie może być wywoływana arbitralnie. Zobacz [ograniczeniami](/windows/desktop/Midl/restricted) atrybutu MIDL, aby uzyskać więcej informacji.

*custom*<br/>
(Opcjonalnie) Co najmniej jeden atrybut; jest to podobne do [niestandardowe](custom-cpp.md) atrybutu. Pierwszy parametr *niestandardowe* jest identyfikatorem GUID atrybutu. Na przykład:

```
[module(custom={guid,1}, custom={guid1,2})]
```

*resource_name*<br/>
Identyfikator ciągu zasobu w pliku .rgs używane do rejestrowania Identyfikatora aplikacji, które biblioteki dll, pliku wykonywalnego lub usługi. Gdy moduł jest typu "Usługa", ten argument jest również używany do uzyskania Identyfikatora ciągu zawierającego nazwę usługi.

> [!NOTE]
> Ciąg zawierający nazwę usługi i pliku .rgs powinien zawierać taką samą wartość liczbową.

## <a name="remarks"></a>Uwagi

Chyba że określisz *ograniczeniami* parametr [emitidl](emitidl.md), **modułu** jest wymagany w przypadku dowolnego programu, który używa atrybutów języka C++.

Blok biblioteka zostanie utworzony, jeśli, oprócz **modułu** atrybutów, kod źródłowy używa również [dispinterface](dispinterface.md), [podwójną](dual.md), [obiektu](object-cpp.md), lub atrybut, który oznacza [coclass](coclass.md).

Jeden blok biblioteki jest dozwolona w pliku .idl. Wiele wpisów modułu w kodzie źródłowym zostaną scalone przy użyciu najbardziej aktualnych wartości parametrów są implementowane.

Jeśli ten atrybut jest używany w projekcie, który korzysta z biblioteki ATL, zachowanie zmiany atrybutów. Oprócz powyższych zachowanie atrybutu są wstawiane obiektów globalnych (o nazwie `_AtlModule`) poprawnego typu i kodu dodatkowej pomocy technicznej. Jeśli ten atrybut jest autonomiczna, wstawia klasa pochodzi od typu modułu. Jeśli ten atrybut jest stosowany do klasy, dodaje klasę bazową typu modułu. Niepoprawny typ jest określana przez wartość *typu* parametru:

- `type` = **dll**

   [CAtlDllModuleT](../../atl/reference/catldllmodulet-class.md) służy jako klasa podstawowa i standardowa wejścia biblioteki DLL punktów wymaganych dla serwera COM. Te punkty wejścia są [DllMain](/windows/desktop/Dlls/dllmain), [DllRegisterServer](/windows/desktop/api/olectl/nf-olectl-dllregisterserver), [DllUnRegisterServer](/windows/desktop/api/olectl/nf-olectl-dllunregisterserver), [DllCanUnloadNow](/windows/desktop/api/combaseapi/nf-combaseapi-dllcanunloadnow), i [ DllGetClassObject](https://msdn.microsoft.com/library/windows/desktop/dd797891).

- `type` = **exe**

   [CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md) służy jako klasa bazowa i punktu wejścia pliku wykonywalnego standardowa [WinMain](/windows/desktop/api/winbase/nf-winbase-winmain).

- `type` = **Usługa**

   [CAtlServiceModuleT](../../atl/reference/catlservicemodulet-class.md) służy jako klasa bazowa i punktu wejścia pliku wykonywalnego standardowa [WinMain](/windows/desktop/api/winbase/nf-winbase-winmain).

- `type` = **Nie określono tego parametru**

   Wyłącza iniekcji kodu biblioteki ATL, powiązany z atrybutem modułu.

## <a name="example"></a>Przykład

Poniższy kod przedstawia sposób tworzenia blok biblioteki w pliku .idl wygenerowany.

```cpp
// cpp_attr_ref_module1.cpp
// compile with: /LD
[module(name="MyLibrary", version="1.2", helpfile="MyHelpFile")];
```

Poniższy kod pokazuje, że może zapewnić implementacji funkcji, która będzie wyświetlana w kodzie, który został wprowadzony w wyniku użycia **modułu**. Zobacz [/Fx](../../build/reference/fx-merge-injected-code.md) Aby uzyskać więcej informacji o wyświetlaniu wprowadzonego kodu. Aby zastąpić jedną z funkcji wstawione przez **modułu** atrybutu, wybierz klasę, która będzie zawierać implementacji funkcji upewnij **modułu** atrybut zastosowania do tej klasy.

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
|**Dotyczy**|Dowolne miejsce|
|**Powtarzalne**|Nie|
|**Wymaganych atrybutów**|Brak|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji, zobacz [konteksty atrybutu](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz też

[Atrybuty IDL](idl-attributes.md)<br/>
[Atrybuty klasy](class-attributes.md)<br/>
[Oddzielne atrybuty](stand-alone-attributes.md)<br/>
[Atrybuty Typedef, Enum, Union oraz Struct](typedef-enum-union-and-struct-attributes.md)<br/>
[usesgetlasterror](usesgetlasterror.md)<br/>
[Biblioteka](/windows/desktop/Midl/library)<br/>
[helpcontext](helpcontext.md)<br/>
[helpstring](helpstring.md)<br/>
[helpfile](helpfile.md)<br/>
[version](version-cpp.md)