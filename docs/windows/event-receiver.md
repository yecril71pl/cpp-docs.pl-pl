---
title: event_receiver | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- vc-attr.event_receiver
dev_langs:
- C++
helpviewer_keywords:
- event_receiver attribute
- event receivers
- events [C++], event receivers (sinks)
- event handling [C++], attributes
- event handling [C++], creating receiver
- event sinks, creating
- event sinks
ms.assetid: bf8fe770-3ea2-4128-b46b-166222ee4097
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 50ea26172e2f5112e760aa02d9247d07afbead2b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="eventreceiver"></a>event_receiver
Tworzy odbiorcy zdarzeń (zbiornika).  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      [ event_receiver(  
   type   
   [, layout_dependent=false]   
) ]  
```  
  
#### <a name="parameters"></a>Parametry  
 `type`  
 Wyliczenie jednego z następujących wartości:  
  
-   `native`dla niezarządzanego kodu C/C++ (domyślnie klasach macierzystych).  
  
-   `com`dla modelu COM kodu. Ta wartość wymaga, aby uwzględnić następujące pliki nagłówka:  
  
    ```  
    #define _ATL_ATTRIBUTES  
    #include <atlbase.h>  
    #include <atlcom.h>  
    ```  
  
 **layout_dependent**  
 Określ *layout_dependent* tylko wtedy, gdy `type` = **com**. *layout_dependent* jest wartością logiczną:  
  
-   **wartość true,** oznacza, że podpis delegatów w przypadku odbiornika musi dokładnie odpowiadać te, do których one są argumentów podłączono zdarzeń źródła. Nazwy obsługi odbiorcy zdarzeń muszą być zgodne nazw określonych w interfejsie źródłowym odpowiednie zdarzenie. Należy użyć **coclass** podczas *layout_dependent* jest **true**. Jest nieco bardziej wydajne, aby określić **true**.  
  
-   **FALSE** (ustawienie domyślne) oznacza, że wywołanie klasy Konwencji i magazynu (wirtualny, statyczne i inne) nie musi odpowiadać metoda zdarzenia i procedurami obsługi; ani zbędna nazwy programu obsługi do dopasowania nazwy metod interfejsu źródła zdarzeń.  
  
## <a name="remarks"></a>Uwagi  
 **Event_receiver** atrybutu C++ Określa, czy klasy lub struktury, do którego jest stosowana będzie odbiornik zdarzeń przy użyciu modelu ujednoliconego zdarzeń Visual C++.  
  
 **event_receiver** jest używany z [event_source —](../windows/event-source.md) atrybutu i [__hook](../cpp/hook.md) i [__unhook](../cpp/unhook.md) słów kluczowych. Użyj **event_source —** można utworzyć źródła zdarzeń. Użyj `__hook` w metodach odbiornik zdarzeń do skojarzenia metody odbiorcy zdarzeń ("haku") do zdarzeń źródła zdarzenia. Użyj `__unhook` można usunąć skojarzenia je.  
  
 *layout_dependent* określić tylko dla odbiorcy zdarzeń COM (`type`=**com**). Wartość domyślna dla *layout_dependent* jest **false**.  
  
> [!NOTE]
>  Szablonu klasy lub struktury nie mogą zawierać zdarzenia.  
  
## <a name="requirements"></a>Wymagania  
  
### <a name="attribute-context"></a>Atrybut kontekstu  
  
|||  
|-|-|  
|**Dotyczy**|**Klasa**,`struct`|  
|**Powtarzalne**|Nie|  
|**Wymaganych atrybutów**|**coclass** podczas *layout_dependent*=**true**|  
|**Nieprawidłowe atrybuty**|Brak|  
  
 Aby uzyskać więcej informacji, zobacz [konteksty atrybutu](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Atrybuty kompilatora](../windows/compiler-attributes.md)   
 [event_source —](../windows/event-source.md)   
 [__Event](../cpp/event.md)   
 [__hook](../cpp/hook.md)   
 [__unhook](../cpp/unhook.md)   
 [Atrybuty klasy](../windows/class-attributes.md)   
