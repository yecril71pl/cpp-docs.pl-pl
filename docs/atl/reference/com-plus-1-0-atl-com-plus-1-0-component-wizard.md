---
title: Model COM + 1.0, Kreator składnika ATL COM + 1.0 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.codewiz.class.atl.mts.options
dev_langs:
- C++
ms.assetid: 2fbe259c-6be1-4d0e-9cfe-721c75c97cb1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9a23f148fbdc611c8a11d8116b2e7dff34fc9d8f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32358215"
---
# <a name="com-10-atl-com-10-component-wizard"></a>Model COM + 1.0, Kreator składnika ATL COM + 1.0
Użyj tej strony ATL COM + 1.0 składnik kreatora, aby określić typ interfejsu i dodatkowe interfejsy do obsługi.  
  
 Aby uzyskać więcej informacji dotyczących projektów ATL i klasy ATL COM, zobacz [ATL COM — składniki pulpitu](../../atl/atl-com-desktop-components.md).  
  
 **Interface**  
 Wskazuje typ interfejsu, który obsługuje obiektu. Domyślnie obiekt obsługuje dwa interfejsu.  
  
|Opcja|Opis|  
|------------|-----------------|  
|**Dual**|Określa, że obiekt obsługuje dwa interfejsu (jego vtable ma niestandardowy interfejs funkcje i późne powiązania `IDispatch` metody). Umożliwia COM klientów i automatyzację kontrolerów dostępu do tego obiektu.|  
|**Niestandardowy**|Określa, że obiekt obsługuje niestandardowy interfejs (jego vtable ma funkcje niestandardowy interfejs). Niestandardowy interfejs może być szybsza niż dwa interfejsu, szczególnie w granicach procesu.<br /><br /> -   **Automatyzacja zgodne** dodaje obsługę automatyzacji do niestandardowego interfejsu. Oparte na atrybutach projektów, ustawia **oleautomation** atrybut klasy coclass.|  
  
 **Kolejkowane**  
 Wskazuje, czy klienci mogą wywoływać ten składnik asynchronicznie, używając kolejek wiadomości. Dodaje składnik przypisane niestandardowe makra (TLBATTR_QUEUEABLE, 0) do pliku .h (Projekty oparte na atrybutach) lub do pliku .idl (nonattributed projektów).  
  
 **Obsługa**  
 Określa dodatkowe wsparcie dla obiekt i obsługi kontroli błędów.  
  
|Opcja|Opis|  
|------------|-----------------|  
|**ISupportErrorInfo**|Tworzy obsługę [ISupportErrorInfo](../../atl/reference/isupporterrorinfoimpl-class.md) interfejsu, obiekt można zwrócić informacje o błędzie do klienta.|  
|**IObjectControl**|Zapewnia dostęp do trzech obiektu [IObjectControl](http://msdn.microsoft.com/library/windows/desktop/ms686474) metody: [Aktywuj](http://msdn.microsoft.com/library/windows/desktop/ms681303), [CanBePooled](http://msdn.microsoft.com/library/windows/desktop/ms684322), i [Dezaktywuj](http://msdn.microsoft.com/library/windows/desktop/ms687094).|  
|**IObjectConstruct**|Tworzy obsługę [IObjectConstruct](http://msdn.microsoft.com/library/windows/desktop/ms680583) interfejsu do zarządzania przekazywanie parametrów z innych metod lub obiektów.|  
  
 **Transakcja**  
 Wskazuje, że obiekt obsługuje transakcji. Zawiera mtxattr.h pliku w pliku .idl (nonattributed projektów).  
  
|Opcja|Opis|  
|------------|-----------------|  
|**Obsługiwane**|Określa, że obiekt jest nigdy głównego strumienia transakcji przez dodanie custom(TLBATTR_TRANS_SUPPORTED,0) makro atrybutu składnika do pliku .h (Projekty oparte na atrybutach) lub do pliku .idl (nonattributed projektów).|  
|**Wymagane**|Określa, że obiekt może lub nie może być głównego strumienia transakcji przez dodanie custom(TLBATTR_TRANS_REQUIRED,0) makro atrybutu składnika do pliku .h (Projekty oparte na atrybutach) lub do pliku .idl (nonattributed projektów).|  
|**Nieobsługiwane**|Określa, że obiekt wyklucza transakcji. Dodaje custom(TLBATTR_TRANS_NOTSUPP,0) makro atrybutu składnika do pliku .h (Projekty oparte na atrybutach) lub do pliku .idl (nonattributed projektów).|  
|**Wymagane nowe**|Określa, że obiekt jest zawsze głównego strumienia transakcji przez dodanie custom(TLBATTR_TRANS_REQNEW,0) makro atrybutu składnika do pliku .h (Projekty oparte na atrybutach) lub do pliku .idl (nonattributed projektów).|  
  
## <a name="see-also"></a>Zobacz też  
 [ATL COM + 1.0 Kreator składników stron ASP](../../atl/reference/atl-com-plus-1-0-component-wizard.md)   
 [Składnik ATL COM + 1.0](../../atl/reference/adding-an-atl-com-plus-1-0-component.md)

