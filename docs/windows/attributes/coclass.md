---
title: Klasa coclass (atrybut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.coclass
helpviewer_keywords:
- coclass attribute
ms.assetid: 42da6a10-3af9-4b43-9a1d-689d00b61eb3
ms.openlocfilehash: e1f99a2780ab4f451533a3e797e473f60680c6ab
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "59035205"
---
# <a name="coclass"></a>coclass

Tworzy obiekt COM, które można zaimplementować interfejsu COM.

## <a name="syntax"></a>Składnia

```cpp
[coclass]
```

## <a name="remarks"></a>Uwagi

**Coclass** atrybut C++ umieszcza konstrukcję klasy coclass w pliku .idl wygenerowany.

Podczas definiowania klasy coclass, można również określić [uuid](uuid-cpp-attributes.md), [wersji](version-cpp.md), [wątkowości](threading-cpp.md), [vi_progid —](vi-progid.md), i [progid ](progid.md) atrybutów. Jednym z nich nie jest określona, zostanie wygenerowany.

Jeśli dwa pliki nagłówkowe zawierają klasach z atrybutem **coclass** atrybutu i określać identyfikator GUID, kompilator będzie używał tego samego identyfikatora GUID dla obu klas i który spowoduje błąd MIDL.  Dlatego należy używać `uuid` atrybutu, gdy używasz **coclass**.

**Projekty ATL**

Gdy ten atrybut poprzedza definicji klasy lub struktury w projekcie ATL go:

- Wprowadza kodu lub danych w celu obsługi rejestracji automatycznej dla tego obiektu.

- Wprowadza kodu lub danych w celu obsługi COM fabryki klas dla obiektu.

- Wprowadza kod lub dane, aby zaimplementować `IUnknown` i obiekt COM możliwość utworzenia obiektu.

W szczególności następujące klasy bazowe są dodawane do obiektu docelowego:

- [Klasa CComCoClass](../../atl/reference/ccomcoclass-class.md) udostępnia klasy domyślny model fabryki i agregację dla obiektu.

- [Klasa CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md) znajduje się szablon, na podstawie klasy modelu wątkowości, określony przez [wątkowości](threading-cpp.md) atrybutu. Jeśli `threading` atrybut nie jest określony, domyślny model wątkowości typu apartment.

- [IProvideClassInfo2Impl](../../atl/reference/iprovideclassinfo2impl-class.md) jest dodana gdy [noncreatable —](noncreatable.md) atrybut nie jest określony dla obiektu docelowego.

Na koniec podwójnego interfejsu, który nie został zdefiniowany przy użyciu osadzonych IDL zostaje zastąpiona opcją odpowiednich [IDispatchImpl](../../atl/reference/idispatchimpl-class.md) klasy. Jeśli podwójnego interfejsu jest zdefiniowany w osadzonych IDL, konkretnego interfejsu na liście bazowych nie jest modyfikowany.

**Coclass** atrybutu sprawia, że następujące funkcje dostępne za pośrednictwem wprowadzonego kodu lub w przypadku `GetObjectCLSID`, jako metody statycznej w klasie bazowej `CComCoClass`:

- `UpdateRegistry` rejestruje fabryki klas klasy docelowej.

- `GetObjectCLSID`, która jest powiązana z rejestracją, można również uzyskać identyfikator CLSID klasy docelowej.

- `GetObjectFriendlyName` Domyślnie zwraca ciąg formatu "\<*Nazwa klasy docelowej*> `Object`". Jeśli ta funkcja jest już istnieje, nie został dodany. Dodaj tę funkcję do klasy docelowej, aby powrócić do bardziej przyjaznej nazwy, niż generowane automatycznie.

- `GetProgID`, która jest powiązana z rejestracją, zwraca ciąg określony za pomocą [progid](progid.md) atrybutu.

- `GetVersionIndependentProgID` ma taką samą funkcjonalność jak `GetProgID`, ale zwraca ciąg określony za pomocą [vi_progid —](vi-progid.md).

Następujące zmiany, które są związane z mapy interfejsu COM, zostały wprowadzone do klasy docelowej:

- Mapy COM jest dodawana z wpisy dla wszystkich interfejsów pochodną klasy docelowej i wszystkie wpisy określone przez [punkty wejścia interfejsu COM](../../mfc/com-interface-entry-points.md) atrybutu lub wymagane przez [agregacje](aggregates.md) atrybutu.

- [OBJECT_ENTRY_AUTO](../../atl/reference/object-map-macros.md#object_entry_auto) makra są wstawiane do mapy COM.

Nazwa klasy coclass wygenerowane w pliku .idl dla klasy będzie mieć taką samą nazwę jak klasa.  Na przykład i odwołujące się do poniższego przykładu, dostęp do Identyfikatora klasy dla klasy coclass `CMyClass`, w kliencie za pomocą pliku nagłówka wygenerowane w MIDL, należy użyć `CLSID_CMyClass`.

## <a name="example"></a>Przykład

Poniższy kod przedstawia sposób użycia **coclass** atrybutu:

```cpp
// cpp_attr_ref_coclass1.cpp
// compile with: /LD
#include "unknwn.h"
[module(name="MyLib")];

[ object, uuid("00000000-0000-0000-0000-000000000001") ]
__interface I {
   HRESULT func();
};

[coclass, progid("MyCoClass.coclass.1"), vi_progid("MyCoClass.coclass"),
appobject, uuid("9E66A294-4365-11D2-A997-00C04FA37DDB")]
class CMyClass : public I {};
```

Poniższy przykład przedstawia sposób przesłonięcia Domyślna implementacja funkcji, która pojawia się w kodzie wstrzyknięte przez **coclass** atrybutu. Zobacz [/Fx](../../build/reference/fx-merge-injected-code.md) Aby uzyskać więcej informacji o wyświetlaniu wprowadzonego kodu. Wszystkie klasy podstawowe lub interfejsów, których używasz dla klasy będą wyświetlane w wprowadzonego kodu. Dodatkowo Jeśli klasa jest domyślnie włączone w wprowadzonego kodu, możesz jawnie określić tę klasę jako podstawa dla swojej klasy coclass dostawca atrybucie użyje formularza, określonych w kodzie.

```cpp
// cpp_attr_ref_coclass2.cpp
// compile with: /LD
#include <atlbase.h>
#include <atlcom.h>
#include <atlwin.h>
#include <atltypes.h>
#include <atlctl.h>
#include <atlhost.h>
#include <atlplus.h>

[module(name="MyLib")];

[object, uuid("00000000-0000-0000-0000-000000000000")]
__interface bb {};

[coclass, uuid("00000000-0000-0000-0000-000000000001")]
class CMyClass : public bb {
public:
   // by adding the definition of UpdateRegistry to your code, // the function will not be included in the injected code
   static HRESULT WINAPI UpdateRegistry(BOOL bRegister) {
      // you can add to the default implementation
      CRegistryVirtualMachine rvm;
      HRESULT hr;
      if (FAILED(hr = rvm.AddStandardReplacements()))
         return hr;
      rvm.AddReplacement(_T("FriendlyName"), GetObjectFriendlyName());
      return rvm.VMUpdateRegistry(GetOpCodes(), GetOpcodeStringVals(),       GetOpcodeDWORDVals(), GetOpcodeBinaryVals(), bRegister);
   }
};
```

## <a name="requirements"></a>Wymagania

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Informacje zawarte w tym artykule dotyczą**|**Klasa**, **— struktura**|
|**Powtarzalne**|Nie|
|**Wymaganych atrybutów**|Brak|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji na temat konteksty atrybutu zobacz [konteksty atrybutu](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz także

[atrybuty IDL](idl-attributes.md)<br/>
[Atrybuty COM](com-attributes.md)<br/>
[Atrybuty klasy](class-attributes.md)<br/>
[Atrybuty Typedef, Enum, Union oraz Struct](typedef-enum-union-and-struct-attributes.md)<br/>
[appobject](appobject.md)