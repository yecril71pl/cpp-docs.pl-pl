---
title: event_source | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.event_source
dev_langs:
- C++
helpviewer_keywords:
- event handling, attributes
- event logs, event source
- event sources, creating
- event_source attribute
- event sources
- event handling, creating event source
ms.assetid: 0983e36a-6127-4fbb-8a22-8dfec6564c16
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e44b5757ea7b9e469275688443ba7ed1e3810571
ms.sourcegitcommit: d5d6bb9945c3550b8e8864b22b3a565de3691fde
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/06/2018
ms.locfileid: "39571392"
---
# <a name="eventsource"></a>event_source
Tworzy źródła zdarzenia.  
  
## <a name="syntax"></a>Składnia  
  
```  
[ event_source(  
   type,  
   optimize=[speed | size],  
   decorate=[true | false]  
) ]  
```  
  
### <a name="parameters"></a>Parametry  
 *Typ*  
 Wyliczenie jednego z następujących wartości:  
  
-   `native` dla niezarządzanego kodu C/C++ (wartość domyślna dla klasy niezarządzane).  
  
-   `com` dla kodu COM. Należy użyć `coclass` podczas `type` = `com`. Ta wartość wymaga, że zawrzesz następujące pliki nagłówków:  
  
    ```  
    #define _ATL_ATTRIBUTES  
    #include <atlbase.h>  
    #include <atlcom.h>  
    ```  
  
 *optymalizuj*  
 Gdy *typu* jest `native`, można określić `optimize=size`, aby wskazać, że istnieje 4 bajty pamięci masowej (minimum) dla wszystkich zdarzeń w klasie lub `optimize=speed` (ustawienie domyślne), aby wskazać, że jest 4 * (liczba zdarzeń) bajtów magazynu.  
  
 *dekoracji*  
 Gdy *typu* jest `native`, można określić `decorate=false`, aby wskazać, że rozwiniętej nazwy w pliku scalonego (.mrg) nie powinna zawierać nazwę klasy otaczającej. [/FX](../build/reference/fx-merge-injected-code.md) umożliwia generowanie plików .mrg. `decorate=false`, która jest wartością domyślną, wyniki w pełni kwalifikowanego typu nazwy w scalony plik.  
  
## <a name="remarks"></a>Uwagi  
 **Event_source** atrybut C++ Określa, że klasy lub struktury, do którego jest stosowana będzie źródła zdarzenia.  
  
 **event_source** jest używany w połączeniu z [event_receiver](../windows/event-receiver.md) atrybutu i [__event](../cpp/event.md) — słowo kluczowe. Użyj `event_receiver` do tworzenia odbiorcy zdarzeń. Użyj **__event** metod w źródle zdarzenia do określenia tych metod jako zdarzenia.  
  
> [!NOTE]
>  Szablonem klasy lub struktury nie mogą zawierać zdarzenia.  
  
## <a name="requirements"></a>Wymagania  
  
### <a name="attribute-context"></a>Kontekst atrybutu  
  
|||  
|-|-|  
|**Dotyczy**|**Klasa**, **— struktura**|  
|**Powtarzalne**|Nie|  
|**Wymaganych atrybutów**|**Klasa coclass** po `type`=`com`|  
|**Nieprawidłowe atrybuty**|Brak|  
  
 Aby uzyskać więcej informacji, zobacz [konteksty atrybutu](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Atrybuty kompilatora](../windows/compiler-attributes.md)   
 [event_receiver](../windows/event-receiver.md)   
 [__Event](../cpp/event.md)   
 [__hook](../cpp/hook.md)   
 [__unhook](../cpp/unhook.md)   
 [Atrybuty klasy](../windows/class-attributes.md)   