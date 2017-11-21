---
title: "Moduł (C++) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: vc-attr.module
dev_langs: C++
helpviewer_keywords: module attributes
ms.assetid: 02223b2a-62b5-4262-832f-564b1e11e58e
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 8f5c751bffbc8ae7c5dc71ab507ed878fc94d82d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="module-c"></a>moduł (C++)
Określa blok biblioteki w pliku .idl.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
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
  
#### <a name="parameters"></a>Parametry  
 ***Typ*** (opcjonalnie)  
 Może to być jedna z następujących czynności:  
  
-   **biblioteki dll** dodaje funkcje i klasy, które umożliwiają wynikowa Biblioteka DLL do działania jako serwer COM w trakcie. Jest to wartość domyślna.  
  
-   **exe** dodaje funkcje i klasy, które umożliwiają powstałe w ten sposób wykonywalnego mógł działać jako poza serwer COM procesu.  
  
-   **Usługa** dodaje funkcje i klasy, które umożliwiają powstałe w ten sposób pliku wykonywalnego do działania jako usługa NT.  
  
-   **Nieokreślony** wyłącza iniekcji kodu biblioteki ATL powiązany z atrybutem modułu: iniekcji klasy modułu ATL, globalne wystąpienie _AtlModule i wpis punktu funkcji.  Pozostawienie iniekcji kodu biblioteki ATL z powodu innych atrybutów w projekcie.  
  
 ***Nazwa*** (opcjonalnie)  
 Nazwa bloku biblioteki.  
  
 ***Wersja*** (opcjonalnie)  
 Numer wersji, który ma zostać przypisany do bloku biblioteki. Wartość domyślna to 1.0.  
  
 `uuid`  
 Unikatowy identyfikator w bibliotece. Jeśli ten parametr zostanie pominięty, identyfikator będą automatycznie generowane w bibliotece. Należy pobrać *uuid* bloku biblioteki można wykonać za pomocą identyfikatora **__uuidof (***libraryname***)**.  
  
 **Identyfikator LCID**  
 Parametr lokalizacja. Zobacz [lcid](http://msdn.microsoft.com/library/windows/desktop/aa367067) Aby uzyskać więcej informacji.  
  
 **formant** (opcjonalnie)  
 Określa, czy formanty wszystkie klasy coclass w bibliotece.  
  
 **HelpString —**  
 Określa bibliotekę typów.  
  
 ***helpstringdll —*** (opcjonalnie)  
 Ustawia nazwę plik .dll, który będzie używany do wyszukiwania ciągów dokumentu. Zobacz [helpstringdll —](http://msdn.microsoft.com/library/windows/desktop/aa366860) Aby uzyskać więcej informacji.  
  
 **HelpFile** (opcjonalnie)  
 Nazwa pliku pomocy dla biblioteki typów.  
  
 **helpcontext** (opcjonalnie)  
 Identyfikator pomocy dla tego typu biblioteki.  
  
 **helpstringcontext —** (opcjonalnie)  
 Zobacz [helpstringcontext —](../windows/helpstringcontext.md) Aby uzyskać więcej informacji.  
  
 **ukryte** (opcjonalnie)  
 Uniemożliwia wyświetlanie całej biblioteki. To użycie jest przeznaczony do użytku z formantami. Hosty muszą Utwórz nową bibliotekę typu, który opakowuje formantu o rozszerzonych właściwości. Zobacz [ukryte](http://msdn.microsoft.com/library/windows/desktop/aa366861) atrybutu MIDL, aby uzyskać więcej informacji.  
  
 **ograniczone** (opcjonalnie)  
 Elementy członkowskie biblioteki nie może być wywoływana arbitralnie. Zobacz [ograniczeniami](http://msdn.microsoft.com/library/windows/desktop/aa367157) atrybutu MIDL, aby uzyskać więcej informacji.  
  
 ***niestandardowe*** (opcjonalnie)  
 Co najmniej jeden atrybut; jest to podobne do [niestandardowych](../windows/custom-cpp.md) atrybutu. Pierwszy parametr `custom` jest identyfikatorem GUID atrybutu. Na przykład:  
  
```  
[module(custom={guid,1}, custom={guid1,2})]  
```  
  
 **resource_name**  
 Identyfikator zasobu ciągu pliku .rgs umożliwia zarejestrowanie tego Identyfikatora aplikacji biblioteki dll, pliku wykonywalnego lub usługi. Jeśli moduł jest typ usługi, ten argument umożliwia również uzyskać identyfikator ciągu zawierającego nazwę usługi.  
  
> [!NOTE]
>  Zarówno w pliku .rgs, jak i w ciągu zawierającego nazwę usługi powinny zawierać taką samą wartość liczbową.  
  
## <a name="remarks"></a>Uwagi  
 O ile nie zostanie określony **ograniczone** parametr [emitidl](../windows/emitidl.md), **modułu** jest wymagany w program, który używa atrybutów języka C++.  
  
 Blok biblioteki zostanie utworzony, jeśli oprócz **modułu** atrybutu, kod źródłowy używa również [dispinterface](../windows/dispinterface.md), [podwójną](../windows/dual.md), [obiektu](../windows/object-cpp.md), lub atrybut, który oznacza [coclass](../windows/coclass.md).  
  
 Jeden blok biblioteki jest dozwolony w pliku .idl. Wiele wpisów modułu w kodzie źródłowym zostaną scalone z ostatnich wartości parametru implementowana.  
  
 Jeśli ten atrybut jest używany w projekcie, który używa ATL, zachowanie zmiany atrybutów. Oprócz powyższych zachowanie atrybutu również Wstawia obiekt global (o nazwie **_AtlModule**) poprawnego typu i dodatkowe wsparcie kodu. Jeśli ten atrybut jest autonomiczny, wstawia klasa pochodzi od typu modułu. Jeśli ten atrybut jest stosowany do klasy, dodaje klasę podstawową typu modułu. Niepoprawny typ jest określana przez wartość `type` parametru:  
  
-   `type` = **biblioteki dll**  
  
     [CAtlDllModuleT](../atl/reference/catldllmodulet-class.md) jest używany jako klasa podstawowa i standardowa wejścia biblioteki DLL punktów wymagane przez serwer COM. Te punkty wejścia są [DllMain](http://msdn.microsoft.com/library/windows/desktop/ms682583), [DllRegisterServer](http://msdn.microsoft.com/library/windows/desktop/ms682162), [DllUnRegisterServer](http://msdn.microsoft.com/library/windows/desktop/ms691457), [DllCanUnloadNow](http://msdn.microsoft.com/library/windows/desktop/ms690368), i [ Metody DllGetClassObject](http://msdn.microsoft.com/library/windows/desktop/dd797891).  
  
-   `type` = **wywołanie pliku exe**  
  
     [CAtlExeModuleT](../atl/reference/catlexemodulet-class.md) jest używany jako klasa podstawowa i punkt wejścia pliku wykonywalnego standardowe [WinMain](http://msdn.microsoft.com/library/windows/desktop/ms633559).  
  
-   `type` = **usługi**  
  
     [CAtlServiceModuleT](../atl/reference/catlservicemodulet-class.md) jest używany jako klasa podstawowa i punkt wejścia pliku wykonywalnego standardowe [WinMain](http://msdn.microsoft.com/library/windows/desktop/ms633559).  
  
-   `type` = **nieokreślone**  
  
     Wyłącza iniekcji kodu biblioteki ATL powiązany z atrybutem modułu.  
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia sposób tworzenia blok biblioteki w pliku .idl wygenerowany.  
  
```  
// cpp_attr_ref_module1.cpp  
// compile with: /LD  
[module(name="MyLibrary", version="1.2", helpfile="MyHelpFile")];  
```  
  
 Poniższy kod przedstawia zapewniają implementacji funkcji, która będzie wyświetlana na kod, który został wprowadzonym w wyniku użycia **modułu**. Zobacz [/Fx](../build/reference/fx-merge-injected-code.md) Aby uzyskać więcej informacji o wyświetlaniu wprowadzony kod. Aby zastąpić jedną z funkcji wstawiane przez **modułu** atrybutu, należy klasa, która będzie zawierać implementacji funkcji i upewnij **modułu** atrybutu dotyczą tej klasy.  
  
```  
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
  
### <a name="attribute-context"></a>Atrybut kontekstu  
  
|||  
|-|-|  
|**Dotyczy**|Dowolnego miejsca|  
|**Powtarzalne**|Nie|  
|**Wymaganych atrybutów**|Brak|  
|**Nieprawidłowe atrybuty**|Brak|  
  
 Aby uzyskać więcej informacji, zobacz [konteksty atrybutu](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Atrybuty IDL](../windows/idl-attributes.md)   
 [Atrybuty klasy](../windows/class-attributes.md)   
 [Oddzielne atrybuty](../windows/stand-alone-attributes.md)   
 [Element TypeDef, Enum, Unii i struct — atrybuty](../windows/typedef-enum-union-and-struct-attributes.md)   
 [usesgetlasterror —](../windows/usesgetlasterror.md)   
 [Biblioteka](http://msdn.microsoft.com/library/windows/desktop/aa367069)   
 [helpcontext](../windows/helpcontext.md)   
 [HelpString —](../windows/helpstring.md)   
 [HelpFile](../windows/helpfile.md)   
 [Wersja](../windows/version-cpp.md)   
