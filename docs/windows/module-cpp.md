---
title: Moduł (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.module
dev_langs:
- C++
helpviewer_keywords:
- module attributes
ms.assetid: 02223b2a-62b5-4262-832f-564b1e11e58e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6e25f33e882769219200e6b9a6f8a0949a01d661
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42593360"
---
# <a name="module-c"></a>moduł (C++)

Określa blok biblioteki w pliku .idl.

## <a name="syntax"></a>Składnia

```cpp
[ module (
   type=dll,
   name=string,
   version=1.0,
   uuid=uuid,
   lcid=integer,
   control=boolean,
   helpstring=string,
   helpstringdll=string,
   helpfile=string,
   helpcontext=integer,
   helpstringcontext=integer,
   hidden=boolean,
   restricted=boolean,
   custom=string,
   resource_name=string,
) ];
```

### <a name="parameters"></a>Parametry

*Typ* (opcjonalnie)  
Może to być jeden z następujących elementów:

- `dll` Dodaje funkcje i klasy, które umożliwiają wynikowy DLL do działania jako serwer COM w procesie. Jest to wartość domyślna.

- `exe` Dodaje funkcje i klasy, które pozwalają wynikowy pliku wykonywalnego, aby działały jak poza serwer COM przetwarzania.

- `service` Dodaje funkcje i klasy, które pozwalają wynikowy pliku wykonywalnego do działania jako usługa NT.

- `unspecified` Wyłącza iniekcji kodu biblioteki ATL, powiązany z atrybutem modułu: iniekcji modułu ATL klas, _AtlModule globalnego wystąpienia i wpis punktu funkcji. Nie wyłącza iniekcji kodu biblioteki ATL z powodu innych atrybutów w projekcie.

*Nazwa* (opcjonalnie)  
Nazwa bloku biblioteki.

*Wersja* (opcjonalnie)  
Numer wersji, którą chcesz przypisać do bloku biblioteki. Wartość domyślna to 1.0.

*uuid*  
Unikatowy identyfikator dla biblioteki. Jeżeli pominięto ten parametr zostanie automatycznie wygenerowany identyfikator biblioteki. Musisz pobrać *uuid* bloku Biblioteka można wykonać przy użyciu identyfikatora **__uuidof (** *libraryname* **)**.

*lcid*  
Parametr lokalizacji. Zobacz [lcid](http://msdn.microsoft.com/library/windows/desktop/aa367067) Aby uzyskać więcej informacji.

*Kontrolka* (opcjonalnie)  
Określa, że wszystkie klasy coclass w bibliotece kontrolek.

*helpstring*  
Określa plik biblioteki typów.

*helpstringdll —* (opcjonalnie)  
Określa nazwę pliku .dll, aby wykonać wyszukiwanie ciągu dokumentu. Zobacz [helpstringdll —](http://msdn.microsoft.com/library/windows/desktop/aa366860) Aby uzyskać więcej informacji.

*HelpFile —* (opcjonalnie)  
Nazwa **pomocy** pliku biblioteki typów.

*helpcontext —* (opcjonalnie)  
**Identyfikator pomocy** dla tego typu biblioteki.

*helpstringcontext —* (opcjonalnie)  
Zobacz [helpstringcontext —](../windows/helpstringcontext.md) Aby uzyskać więcej informacji.

*ukryte* (opcjonalnie)  
Uniemożliwia wyświetlanie całej biblioteki. To obciążenie jest przeznaczony do użytku z formantami. Hosty muszą Utwórz nową bibliotekę typu, który opakowuje formant z rozszerzonych właściwości. Zobacz [ukryte](http://msdn.microsoft.com/library/windows/desktop/aa366861) atrybutu MIDL, aby uzyskać więcej informacji.

*ograniczone* (opcjonalnie)  
Elementy członkowskie biblioteki nie może być wywoływana arbitralnie. Zobacz [ograniczeniami](http://msdn.microsoft.com/library/windows/desktop/aa367157) atrybutu MIDL, aby uzyskać więcej informacji.

*niestandardowe* (opcjonalnie)  
Co najmniej jeden atrybut; jest to podobne do [niestandardowe](../windows/custom-cpp.md) atrybutu. Pierwszy parametr *niestandardowe* jest identyfikatorem GUID atrybutu. Na przykład:

```
[module(custom={guid,1}, custom={guid1,2})]
```

*resource_name*  
Identyfikator ciągu zasobu w pliku .rgs używane do rejestrowania Identyfikatora aplikacji, które biblioteki dll, pliku wykonywalnego lub usługi. Gdy moduł jest typu "Usługa", ten argument jest również używany do uzyskania Identyfikatora ciągu zawierającego nazwę usługi.

> [!NOTE]
> Ciąg zawierający nazwę usługi i pliku .rgs powinien zawierać taką samą wartość liczbową.

## <a name="remarks"></a>Uwagi

Chyba że określisz *ograniczeniami* parametr [emitidl](../windows/emitidl.md), **modułu** jest wymagany w przypadku dowolnego programu, który używa atrybutów języka C++.

Blok biblioteka zostanie utworzony, jeśli, oprócz **modułu** atrybutów, kod źródłowy używa również [dispinterface](../windows/dispinterface.md), [podwójną](../windows/dual.md), [obiektu](../windows/object-cpp.md), lub atrybut, który oznacza [coclass](../windows/coclass.md).

Jeden blok biblioteki jest dozwolona w pliku .idl. Wiele wpisów modułu w kodzie źródłowym zostaną scalone przy użyciu najbardziej aktualnych wartości parametrów są implementowane.

Jeśli ten atrybut jest używany w projekcie, który korzysta z biblioteki ATL, zachowanie zmiany atrybutów. Oprócz powyższych zachowanie atrybutu są wstawiane obiektów globalnych (o nazwie `_AtlModule`) poprawnego typu i kodu dodatkowej pomocy technicznej. Jeśli ten atrybut jest autonomiczna, wstawia klasa pochodzi od typu modułu. Jeśli ten atrybut jest stosowany do klasy, dodaje klasę bazową typu modułu. Niepoprawny typ jest określana przez wartość *typu* parametru:

- `type` = **biblioteki dll**

   [CAtlDllModuleT](../atl/reference/catldllmodulet-class.md) służy jako klasa podstawowa i standardowa wejścia biblioteki DLL punktów wymaganych dla serwera COM. Te punkty wejścia są [DllMain](http://msdn.microsoft.com/library/windows/desktop/ms682583), [DllRegisterServer](http://msdn.microsoft.com/library/windows/desktop/ms682162), [DllUnRegisterServer](http://msdn.microsoft.com/library/windows/desktop/ms691457), [DllCanUnloadNow](http://msdn.microsoft.com/library/windows/desktop/ms690368), i [ DllGetClassObject](http://msdn.microsoft.com/library/windows/desktop/dd797891).

- `type` = **plik exe**

   [CAtlExeModuleT](../atl/reference/catlexemodulet-class.md) służy jako klasa bazowa i punktu wejścia pliku wykonywalnego standardowa [WinMain](http://msdn.microsoft.com/library/windows/desktop/ms633559).

- `type` = **Usługa**

   [CAtlServiceModuleT](../atl/reference/catlservicemodulet-class.md) służy jako klasa bazowa i punktu wejścia pliku wykonywalnego standardowa [WinMain](http://msdn.microsoft.com/library/windows/desktop/ms633559).

- `type` = **Nie określono tego parametru**

   Wyłącza iniekcji kodu biblioteki ATL, powiązany z atrybutem modułu.

## <a name="example"></a>Przykład

Poniższy kod przedstawia sposób tworzenia blok biblioteki w pliku .idl wygenerowany.

```cpp
// cpp_attr_ref_module1.cpp
// compile with: /LD
[module(name="MyLibrary", version="1.2", helpfile="MyHelpFile")];
```

Poniższy kod pokazuje, że może zapewnić implementacji funkcji, która będzie wyświetlana w kodzie, który został wprowadzony w wyniku użycia **modułu**. Zobacz [/Fx](../build/reference/fx-merge-injected-code.md) Aby uzyskać więcej informacji o wyświetlaniu wprowadzonego kodu. Aby zastąpić jedną z funkcji wstawione przez **modułu** atrybutu, wybierz klasę, która będzie zawierać implementacji funkcji upewnij **modułu** atrybut zastosowania do tej klasy.

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

Aby uzyskać więcej informacji, zobacz [konteksty atrybutu](../windows/attribute-contexts.md).

## <a name="see-also"></a>Zobacz też

[Atrybuty IDL](../windows/idl-attributes.md)  
[Atrybuty klasy](../windows/class-attributes.md)  
[Oddzielne atrybuty](../windows/stand-alone-attributes.md)  
[Atrybuty Typedef, Enum, Union oraz Struct](../windows/typedef-enum-union-and-struct-attributes.md)  
[usesgetlasterror](../windows/usesgetlasterror.md)  
[Biblioteka](http://msdn.microsoft.com/library/windows/desktop/aa367069)  
[helpcontext](../windows/helpcontext.md)  
[helpstring](../windows/helpstring.md)  
[helpfile](../windows/helpfile.md)  
[Wersja](../windows/version-cpp.md)  