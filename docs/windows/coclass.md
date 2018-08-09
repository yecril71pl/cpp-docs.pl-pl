---
title: Klasa coclass | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.coclass
dev_langs:
- C++
helpviewer_keywords:
- coclass attribute
ms.assetid: 42da6a10-3af9-4b43-9a1d-689d00b61eb3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2043ca568f36d7fc0eaaffbf940cabb423de5620
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39647843"
---
# <a name="coclass"></a>coclass
Tworzy obiekt COM, które można zaimplementować interfejsu COM.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
[coclass]  
```  
  
## <a name="remarks"></a>Uwagi  
 **Coclass** atrybut C++ umieszcza konstrukcję klasy coclass w pliku .idl wygenerowany.  
  
 Podczas definiowania klasy coclass, można również określić [uuid](../windows/uuid-cpp-attributes.md), [wersji](../windows/version-cpp.md), [wątkowości](../windows/threading-cpp.md), [vi_progid —](../windows/vi-progid.md), i [progid ](../windows/progid.md) atrybutów. Jednym z nich nie jest określona, zostanie wygenerowany.  
  
 Jeśli dwa pliki nagłówkowe zawierają klasach z atrybutem **coclass** atrybutu i określać identyfikator GUID, kompilator będzie używał tego samego identyfikatora GUID dla obu klas i który spowoduje błąd MIDL.  Dlatego należy używać `uuid` atrybutu, gdy używasz **coclass**.  
  
 **Projekty ATL**  
  
 Gdy ten atrybut poprzedza definicji klasy lub struktury w projekcie ATL go:  
  
-   Wprowadza kodu lub danych w celu obsługi rejestracji automatycznej dla tego obiektu.  
  
-   Wprowadza kodu lub danych w celu obsługi COM fabryki klas dla obiektu.  
  
-   Wprowadza kod lub dane, aby zaimplementować `IUnknown` i obiekt COM możliwość utworzenia obiektu.  
  
 W szczególności następujące klasy bazowe są dodawane do obiektu docelowego:  
  
-   [Klasa CComCoClass](../atl/reference/ccomcoclass-class.md) udostępnia klasy domyślny model fabryki i agregację dla obiektu.  
  
-   [Klasa CComObjectRootEx](../atl/reference/ccomobjectrootex-class.md) znajduje się szablon, na podstawie klasy modelu wątkowości, określony przez [wątkowości](../windows/threading-cpp.md) atrybutu. Jeśli `threading` atrybut nie jest określony, domyślny model wątkowości typu apartment.  
  
-   [IProvideClassInfo2Impl](../atl/reference/iprovideclassinfo2impl-class.md) jest dodana gdy [noncreatable —](../windows/noncreatable.md) atrybut nie jest określony dla obiektu docelowego.  
  
 Na koniec podwójnego interfejsu, który nie został zdefiniowany przy użyciu osadzonych IDL zostaje zastąpiona opcją odpowiednich [IDispatchImpl](../atl/reference/idispatchimpl-class.md) klasy. Jeśli podwójnego interfejsu jest zdefiniowany w osadzonych IDL, konkretnego interfejsu na liście bazowych nie jest modyfikowany.  
  
 **Coclass** atrybutu sprawia, że następujące funkcje dostępne za pośrednictwem wprowadzonego kodu lub w przypadku `GetObjectCLSID`, jako metody statycznej w klasie bazowej `CComCoClass`:  
  
-   `UpdateRegistry` rejestruje fabryki klas klasy docelowej.  
  
-   `GetObjectCLSID`, która jest powiązana z rejestracją, można również uzyskać identyfikator CLSID klasy docelowej.  
  
-   `GetObjectFriendlyName` Domyślnie zwraca ciąg formatu "\<*Nazwa klasy docelowej*> `Object`". Jeśli ta funkcja jest już istnieje, nie został dodany. Dodaj tę funkcję do klasy docelowej, aby powrócić do bardziej przyjaznej nazwy, niż generowane automatycznie.  
  
-   `GetProgID`, która jest powiązana z rejestracją, zwraca ciąg określony za pomocą [progid](../windows/progid.md) atrybutu.  
  
-   `GetVersionIndependentProgID` ma taką samą funkcjonalność jak `GetProgID`, ale zwraca ciąg określony za pomocą [vi_progid —](../windows/vi-progid.md).  
  
 Następujące zmiany, które są związane z mapy interfejsu COM, zostały wprowadzone do klasy docelowej:  
  
-   Mapy COM jest dodawana z wpisy dla wszystkich interfejsów pochodną klasy docelowej i wszystkie wpisy określone przez [punkty wejścia interfejsu COM](../mfc/com-interface-entry-points.md) atrybutu lub wymagane przez [agregacje](../windows/aggregates.md) atrybutu.  
  
-   [OBJECT_ENTRY_AUTO](../atl/reference/object-map-macros.md#object_entry_auto) makra są wstawiane do mapy COM.
  
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
  
 Poniższy przykład przedstawia sposób przesłonięcia Domyślna implementacja funkcji, która pojawia się w kodzie wstrzyknięte przez **coclass** atrybutu. Zobacz [/Fx](../build/reference/fx-merge-injected-code.md) Aby uzyskać więcej informacji o wyświetlaniu wprowadzonego kodu. Wszystkie klasy podstawowe lub interfejsów, których używasz dla klasy będą wyświetlane w wprowadzonego kodu. Dodatkowo Jeśli klasa jest domyślnie włączone w wprowadzonego kodu, możesz jawnie określić tę klasę jako podstawa dla swojej klasy coclass dostawca atrybucie użyje formularza, określonych w kodzie.  
  
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
   // by adding the definition of UpdateRegistry to your code,   
   // the function will not be included in the injected code  
   static HRESULT WINAPI UpdateRegistry(BOOL bRegister) {  
      // you can add to the default implementation  
      CRegistryVirtualMachine rvm;  
      HRESULT hr;  
      if (FAILED(hr = rvm.AddStandardReplacements()))  
         return hr;  
      rvm.AddReplacement(_T("FriendlyName"), GetObjectFriendlyName());  
      return rvm.VMUpdateRegistry(GetOpCodes(), GetOpcodeStringVals(),  
         GetOpcodeDWORDVals(), GetOpcodeBinaryVals(), bRegister);  
   }  
};  
```  
  
## <a name="requirements"></a>Wymagania  
  
### <a name="attribute-context"></a>Kontekst atrybutu  
  
|||  
|-|-|  
|**Dotyczy**|**Klasa**, **— struktura**|  
|**Powtarzalne**|Nie|  
|**Wymaganych atrybutów**|Brak|  
|**Nieprawidłowe atrybuty**|Brak|  
  
 Aby uzyskać więcej informacji na temat konteksty atrybutu zobacz [konteksty atrybutu](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Atrybuty IDL](../windows/idl-attributes.md)   
 [Atrybuty COM](../windows/com-attributes.md)   
 [Atrybuty klasy](../windows/class-attributes.md)   
 [Element TypeDef, Enum, Union i struct — atrybuty](../windows/typedef-enum-union-and-struct-attributes.md)   
 [appobject](../windows/appobject.md)