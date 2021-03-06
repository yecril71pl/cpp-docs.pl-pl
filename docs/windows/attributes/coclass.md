---
title: coclass (atrybut C++ COM)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.coclass
helpviewer_keywords:
- coclass attribute
ms.assetid: 42da6a10-3af9-4b43-9a1d-689d00b61eb3
ms.openlocfilehash: 12f7af195f2282955cb16c1f38d4e512ca0f86cb
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88838883"
---
# <a name="coclass"></a>coclass

Tworzy obiekt COM, który może zaimplementować interfejs COM.

## <a name="syntax"></a>Składnia

```cpp
[coclass]
```

## <a name="remarks"></a>Uwagi

Atrybut **klasy coclass** C++ umieszcza konstrukcję klasy coclass w wygenerowanym pliku IDL.

Podczas definiowania klasy coclass można także określić atrybuty [UUID](uuid-cpp-attributes.md), [wersja](version-cpp.md), [wątkowość](threading-cpp.md), [vi_progid](vi-progid.md)i [ProgID](progid.md) . Jeśli jeden z nich nie zostanie określony, zostanie wygenerowany.

Jeśli dwa pliki nagłówkowe zawierają klasy z atrybutem **klasy coclass** i nie określają identyfikatora GUID, kompilator użyje tego samego identyfikatora GUID dla obu klas i spowoduje błąd MIDL.  W związku z tym należy używać `uuid` atrybutu podczas używania **klasy coclass**.

**Projekty ATL**

Gdy ten atrybut poprzedza definicję klasy lub struktury w projekcie ATL,:

- Wprowadza kod lub dane do obsługi autorejestracji dla obiektu.

- Wprowadza kod lub dane do obsługi fabryki klas COM dla obiektu.

- Wprowadza kod lub dane w celu zaimplementowania `IUnknown` i utworzenia obiektu do utworzenia obiektu com.

W szczególnych przypadkach następujące klasy bazowe są dodawane do obiektu docelowego:

- [Klasa CComCoClass](../../atl/reference/ccomcoclass-class.md) udostępnia domyślną fabrykę klas i model agregacji dla obiektu.

- [Klasa CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md) ma szablon oparty na klasie modelu wątkowego określonej przez atrybut [wątkowości](threading-cpp.md) . Jeśli `threading` atrybut nie jest określony, domyślny model wątkowości jest typu Apartment.

- [IProvideClassInfo2Impl](../../atl/reference/iprovideclassinfo2impl-class.md) jest dodawany, jeśli nie jest [określony atrybut niemożliwy do utworzenia](noncreatable.md) dla obiektu docelowego.

Na koniec wszystkie dwa interfejsy, które nie są zdefiniowane przy użyciu osadzonego IDL, są zastępowane odpowiadającą klasą [IDispatchImpl](../../atl/reference/idispatchimpl-class.md) . Jeśli podwójny interfejs jest zdefiniowany w osadzonym IDL, określony interfejs na liście podstawowej nie jest modyfikowany.

Atrybut **coclass** również udostępnia następujące funkcje za pośrednictwem wstrzykiwanego kodu lub w przypadku `GetObjectCLSID` , jako metoda statyczna w klasie bazowej `CComCoClass` :

- `UpdateRegistry` rejestruje fabryky klas klasy docelowej.

- `GetObjectCLSID`, który jest powiązany z rejestracją, może również służyć do uzyskania identyfikatora CLSID klasy docelowej.

- `GetObjectFriendlyName` Domyślnie zwraca ciąg o formacie " \<*target class name*> `Object` ". Jeśli ta funkcja już istnieje, nie jest dodawana. Dodaj tę funkcję do klasy Target, aby zwrócić nazwę bardziej przyjaznej inną niż wygenerowana automatycznie.

- `GetProgID`, który jest powiązany z rejestracją, zwraca ciąg określony przy użyciu atrybutu [ProgID](progid.md) .

- `GetVersionIndependentProgID` ma takie same funkcje jak `GetProgID` , ale zwraca ciąg określony za pomocą [vi_progid](vi-progid.md).

Następujące zmiany, które są związane z mapą COM, są tworzone w klasie docelowej:

- Zostanie dodana mapa COM z wpisami dla wszystkich interfejsów Klasa docelowa pochodzi od i wszystkie wpisy określone przez atrybut [punkty wejścia interfejsu com](../../mfc/com-interface-entry-points.md) lub wymagane przez atrybut [Aggregates](aggregates.md) .

- Do mapy COM zostanie wstawione makro [OBJECT_ENTRY_AUTO](../../atl/reference/object-map-macros.md#object_entry_auto) .

Nazwa klasy coclass wygenerowanej w pliku. idl dla klasy będzie miała taką samą nazwę jak Klasa.  Na przykład, i odwołując się do poniższego przykładu, aby uzyskać dostęp do identyfikatora klasy dla klasy coclass `CMyClass` , w kliencie za pomocą MIDLego pliku nagłówkowego, użyj `CLSID_CMyClass` .

## <a name="example"></a>Przykład

Poniższy kod pokazuje, jak używać atrybutu **coclass** :

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

Poniższy przykład pokazuje, jak zastąpić domyślną implementację funkcji, która pojawia się w kodzie wstrzykiwanym przez atrybut **klasy coclass** . Zobacz [/FX](../../build/reference/fx-merge-injected-code.md) , aby uzyskać więcej informacji na temat wyświetlania iniekcji kodu. Wszystkie klasy podstawowe lub interfejsy, które są używane dla klasy, będą widoczne w wstrzykiwanym kodzie. Ponadto, jeśli klasa jest uwzględniana domyślnie w wstrzykiwanym kodzie i jawnie określono tę klasę jako podstawową dla klasy coclass, dostawca atrybutów będzie używać formularza określonego w kodzie.

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

| Kontekst atrybutu | Wartość |
|-|-|
|**Dotyczy**|**`class`**, **`struct`**|
|**Powtarzalne**|Nie|
|**Wymagane atrybuty**|Brak|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji na temat kontekstów atrybutów, zobacz [konteksty atrybutów](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz też

[Atrybuty IDL](idl-attributes.md)<br/>
[Atrybuty COM](com-attributes.md)<br/>
[Atrybuty klasy](class-attributes.md)<br/>
[Atrybuty typedef, enum, Union i struct](typedef-enum-union-and-struct-attributes.md)<br/>
[appobject](appobject.md)
