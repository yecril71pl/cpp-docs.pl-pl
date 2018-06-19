---
title: coclass | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 5eb9c7e632151c039b76a0f389cd18c68c0740ab
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33867015"
---
# <a name="coclass"></a>coclass
Tworzy obiekt COM, które można zaimplementować interfejsu COM.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
[coclass]  
  
```  
  
## <a name="remarks"></a>Uwagi  
 **Coclass** atrybutu C++ umieszcza konstrukcję klasy coclass w pliku .idl wygenerowany.  
  
 Podczas definiowania klasy coclass, można również określić [uuid](../windows/uuid-cpp-attributes.md), [wersji](../windows/version-cpp.md), [wątkowość](../windows/threading-cpp.md), [vi_progid —](../windows/vi-progid.md), i [progid ](../windows/progid.md) atrybutów. Jednym z nich nie jest określona, zostanie wygenerowany.  
  
 Jeśli dwa pliki nagłówkowe zawierają klasy z **coclass** atrybutu i nie podaje identyfikator GUID, kompilator użyje tego samego identyfikatora GUID w obu klasach i który spowoduje błąd MIDL.  W związku z tym należy używać `uuid` atrybutu, gdy używasz **coclass**.  
  
 **Projekty ATL**  
  
 Jeśli ten atrybut poprzedza definicji klasy lub struktury w projekcie ATL go:  
  
-   Injects kod lub dane do obsługi rejestracji automatycznej dla tego obiektu.  
  
-   Injects kod lub dane do obsługi fabryki klasy COM dla obiekt.  
  
-   Injects kod lub dane do zaimplementowania **IUnknown** i powoduje, że obiekt COM możliwość utworzenia obiektu.  
  
 W szczególności następujące klasy podstawowej są dodawane do obiektu docelowego:  
  
-   [Klasa klasy CComCoClass](../atl/reference/ccomcoclass-class.md) zawiera klasy domyślny model fabryki i agregację dla obiekt.  
  
-   [Klasa CComObjectRootEx](../atl/reference/ccomobjectrootex-class.md) ma szablon oparty na klasie model wątkowości, określony przez [wątkowość](../windows/threading-cpp.md) atrybutu. Jeśli **wątkowość** atrybut nie jest określony, domyślny model wątkowości typu apartment.  
  
-   [IProvideClassInfo2Impl](../atl/reference/iprovideclassinfo2impl-class.md) jest dodana gdy [noncreatable —](../windows/noncreatable.md) atrybut nie jest określony dla obiektu docelowego.  
  
 Na koniec żadnych podwójną interfejs, który nie jest zdefiniowany przy użyciu osadzonych IDL jest zastępowany odpowiadającego [elementem IDispatchImpl](../atl/reference/idispatchimpl-class.md) klasy. Jeśli dwie interfejsu jest zdefiniowany w osadzonych IDL, konkretnego interfejsu na liście podstawowej nie jest modyfikowany.  
  
 **Coclass** atrybutu także udostępnia następujące funkcje za pomocą wprowadzonego kodu lub w przypadku `GetObjectCLSID`, jako statycznej metody w klasie podstawowej `CComCoClass`:  
  
-   `UpdateRegistry` rejestruje fabryki klas klasy docelowej.  
  
-   `GetObjectCLSID`, która jest powiązana z rejestracją, można również uzyskać identyfikator CLSID klasy docelowej.  
  
-   **GetObjectFriendlyName** domyślnie zwraca ciąg w formacie "\<*nazwę klasy docelowej*> `Object`". Jeśli ta funkcja jest już obecne, nie został dodany. Dodaj tę funkcję do klasy docelowej, aby zwrócić nazwę bardziej przyjazny niż generowane automatycznie.  
  
-   **GetProgID**, która jest powiązana z rejestracji, zwraca ciąg określonego z [progid](../windows/progid.md) atrybutu.  
  
-   **GetVersionIndependentProgID** ma te same funkcje co **GetProgID**, ale zwraca ciąg określony za pomocą [vi_progid —](../windows/vi-progid.md).  
  
 Zostały wprowadzone następujące zmiany, które są powiązane z mapą COM, Klasa docelowa:  
  
-   Dodaje się wpisy dla wszystkich interfejsów pochodną klasy docelowej i wszystkie wpisy określone przez mapy COM [punkty wejścia interfejsu COM](../mfc/com-interface-entry-points.md) atrybutu lub wymagane przez [agreguje](../windows/aggregates.md) atrybutu.  
  
-   [OBJECT_ENTRY_AUTO](../atl/reference/object-map-macros.md#object_entry_auto) makra są wstawiane do mapy COM.
  
 Nazwa klasy coclass w pliku .idl dla klasy generowane będzie mieć taką samą nazwę jak klasa.  Na przykład i odwołujące się do poniższego przykładu Aby uzyskać dostęp do Identyfikatora klasy dla klasy coclass CMyClass, w kliencie za pośrednictwem pliku nagłówka wygenerowane MIDL, należy użyć CLSID_CMyClass.  
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia sposób użycia **coclass** atrybutu:  
  
```  
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
  
 Poniższy przykład przedstawia sposób przesłonięcia domyślną implementację funkcji, która jest wyświetlana w kodzie wstrzyknięte przez **coclass** atrybutu. Zobacz [/Fx](../build/reference/fx-merge-injected-code.md) Aby uzyskać więcej informacji o wyświetlaniu wprowadzony kod. Wszystkie klasy podstawowe lub interfejsów, które używają dla klasy pojawi się wprowadzony kod.   Co więcej Jeśli klasa jest domyślnie włączone w wprowadzony kod, zostaną jawnie określone tej klasy jako podstawa dla Twojego — klasa coclass dostawcy atrybutu będzie formularz określona w kodzie.  
  
```  
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
  
### <a name="attribute-context"></a>Atrybut kontekstu  
  
|||  
|-|-|  
|**Dotyczy**|**Klasa**, `struct`|  
|**Powtarzalne**|Nie|  
|**Wymaganych atrybutów**|Brak|  
|**Nieprawidłowe atrybuty**|Brak|  
  
 Aby uzyskać więcej informacji na temat konteksty atrybutu, zobacz [konteksty atrybutu](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Atrybuty IDL](../windows/idl-attributes.md)   
 [Atrybuty COM](../windows/com-attributes.md)   
 [Atrybuty klasy](../windows/class-attributes.md)   
 [Element TypeDef, Enum, Unii i struct — atrybuty](../windows/typedef-enum-union-and-struct-attributes.md)   
 [appobject](../windows/appobject.md)