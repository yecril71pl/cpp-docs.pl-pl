---
title: "event_source — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: vc-attr.event_source
dev_langs: C++
helpviewer_keywords:
- event handling, attributes
- event logs, event source
- event sources, creating
- event_source attribute
- event sources
- event handling, creating event source
ms.assetid: 0983e36a-6127-4fbb-8a22-8dfec6564c16
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 05371b5c2d9acd091adcbdf81d2994f205e36ef7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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
  
#### <a name="parameters"></a>Parametry  
 `type`  
 Wyliczenie jednego z następujących wartości:  
  
-   `native`dla niezarządzanego kodu C/C++ (domyślnie klasy niezarządzane).  
  
-   `com`dla modelu COM kodu. Należy użyć `coclass` podczas `type` = `com`. Ta wartość wymaga, aby uwzględnić następujące pliki nagłówka:  
  
    ```  
    #define _ATL_ATTRIBUTES  
    #include <atlbase.h>  
    #include <atlcom.h>  
    ```  
  
 **optymalizuj**  
 Gdy `type` jest **natywnego**, można określić **zoptymalizować = rozmiar**, aby wskazać, że istnieje 4 bajty magazynu (minimum) dla wszystkich zdarzeń w klasie lub **optymalizacji = prędkość** (opcja domyślna), aby wskazać, że jest 4 * bajtów (liczba zdarzeń) magazynu.  
  
 **dekoracji**  
 Gdy `type` jest **natywnego**, można określić **dekoracji = false**, aby wskazać, czy rozwiniętą nazwą w pliku scalony (.mrg) nie może zawierać nazwy klasy otaczającej. [/FX](../build/reference/fx-merge-injected-code.md) umożliwia wygenerowanie .mrg plików. **dekoracji = false**, który jest domyślnym, wyników w pełni kwalifikowanego typu nazw scalony plik.  
  
## <a name="remarks"></a>Uwagi  
 **Event_source —** C++ atrybut określa, czy klasy lub struktury, do którego jest stosowana będzie źródła zdarzenia.  
  
 **event_source —** jest używany w połączeniu z [event_receiver](../windows/event-receiver.md) atrybutu i [__event](../cpp/event.md) — słowo kluczowe. Użyj **event_receiver** do tworzenia odbiorcy zdarzeń. Użyj `__event` metod w źródle zdarzeń, aby określić tych metod jako zdarzenia.  
  
> [!NOTE]
>  Szablonu klasy lub struktury nie mogą zawierać zdarzenia.  
  
## <a name="requirements"></a>Wymagania  
  
### <a name="attribute-context"></a>Atrybut kontekstu  
  
|||  
|-|-|  
|**Dotyczy**|**Klasa**,`struct`|  
|**Powtarzalne**|Nie|  
|**Wymaganych atrybutów**|**coclass** podczas `type` = **com**|  
|**Nieprawidłowe atrybuty**|Brak|  
  
 Aby uzyskać więcej informacji, zobacz [konteksty atrybutu](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Atrybuty kompilatora](../windows/compiler-attributes.md)   
 [event_receiver](../windows/event-receiver.md)   
 [__Event](../cpp/event.md)   
 [__hook](../cpp/hook.md)   
 [__unhook](../cpp/unhook.md)   
 [Atrybuty klasy](../windows/class-attributes.md)   
