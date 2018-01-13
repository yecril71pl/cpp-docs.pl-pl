---
title: __unhook | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- __unhook
- __unhook_cpp
dev_langs: C++
helpviewer_keywords:
- event handlers [C++], dissociating events
- __unhook keyword [C++]
ms.assetid: 953a14f3-5199-459d-81e5-fcf015a19878
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1513391aedf9a08cd1ece971d79fd5f6913d406d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="unhook"></a>__unhook
Dissociates metody obsługi zdarzeń.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      long  __unhook(  
   &SourceClass::EventMethod,  
   source,  
   &ReceiverClass::HandlerMethod  
   [, receiver = this]   
);  
long  __unhook(   
   interface,  
   source  
);  
long  __unhook(  
   source   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 **&***SourceClass* `::` *EventMethod*  
 Wskaźnik do metody zdarzeń, z którego odpięcie metoda obsługi zdarzeń:  
  
-   Natywny zdarzenia C++: *SourceClass* jest klasa źródła zdarzeń i *EventMethod* jest zdarzenie.  
  
-   Zdarzenia COM: *SourceClass* jest interfejsem źródła zdarzeń i *EventMethod* jest jedną z metod.  
  
-   Zarządzanych zdarzeń: *SourceClass* jest klasa źródła zdarzeń i *EventMethod* jest zdarzenie.  
  
 `interface`  
 Nazwa interfejsu, jest unhooked z `receiver`, tylko dla odbiorcy zdarzeń COM, w którym *layout_dependent* parametr [event_receiver](../windows/event-receiver.md) atrybutu **true**.  
  
 *źródło*  
 Wskaźnik do wystąpienia źródła zdarzenia. W zależności od kodu `type` określony w **event_receiver**, *źródła* może być jedną z następujących czynności:  
  
-   Wskaźnik obiektu źródła zdarzeń macierzystego.  
  
-   **IUnknown**— na podstawie wskaźnika (COM źródła).  
  
-   Wskaźnik zarządzanego obiektu (w przypadku zarządzanych zdarzeń).  
  
 **&***ReceiverClass* `::``HandlerMethod`  
 Wskaźnik do metoda obsługi zdarzeń za unhooked ze zdarzenia. Program obsługi jest określony jako metody klasy lub odwołanie do tego samego; Jeśli nie określisz nazwy klasy `__unhook` zakłada klasy się, że w którym jest wywoływana.  
  
-   Natywny zdarzenia C++: *ReceiverClass* jest klasy odbiorcy zdarzeń i `HandlerMethod` jest programem obsługi.  
  
-   Zdarzenia COM: *ReceiverClass* jest interfejsem odbiorcy zdarzeń i `HandlerMethod` jest jednym z jego obsługi.  
  
-   Zarządzanych zdarzeń: *ReceiverClass* jest klasy odbiorcy zdarzeń i `HandlerMethod` jest programem obsługi.  
  
 `receiver`(opcjonalnie)  
 Wskaźnik do wystąpienia klasy odbiorcy zdarzeń. Jeśli odbiornik nie zostanie określony, wartością domyślną jest odbiornik klasy lub struktury, w którym `__unhook` jest wywoływana.  
  
## <a name="usage"></a>Użycie  
 Może być używany w żadnych zakresu funkcji, w tym głównym poza klasy odbiorcy zdarzeń.  
  
## <a name="remarks"></a>Uwagi  
 Użyj funkcji wewnętrznej `__unhook` w odbiornik zdarzeń, aby usunąć skojarzenie lub "odpięcie" metody obsługi zdarzeń — metoda.  
  
 Istnieją trzy rodzaje `__unhook`. W większości przypadków, można użyć danego formularza (cztery argument). Można użyć drugiej formy (dwuargumentowej) `__unhook` tylko dla odbiornika zdarzeń COM; to unhooks interfejsu całe zdarzenie. Trzeci formularz (jeden argument) umożliwia Odpięcie wszystkich obiektów delegowanych z określonego źródła.  
  
 Podano niezerowe wartości zwracanej wskazuje, że wystąpił błąd (zdarzeń zarządzanych spowoduje zgłoszenie wyjątku).  
  
 Jeśli należy wywołać `__unhook` na zdarzenia i program obsługi zdarzeń, które nie już argumentów podłączono go nie przyniesie efektu.  
  
 W czasie kompilacji kompilator sprawdza, czy zdarzenie istnieje i czy parametru typu sprawdzenie z określonym programem obsługi.  
  
 Z wyjątkiem zdarzeń COM `__hook` i `__unhook` może być wywołana poza odbiorcy zdarzeń.  
  
 Zamiast `__unhook` jest użycie operatora-=.  
  
 Aby uzyskać informacji na temat kodowania zarządzanych zdarzeń w nowej składni, zobacz [zdarzeń](../windows/event-cpp-component-extensions.md).  
  
> [!NOTE]
>  Szablonu klasy lub struktury nie mogą zawierać zdarzenia.  
  
## <a name="example"></a>Przykład  
 Zobacz [obsługi zdarzeń w natywnym kodzie C++](../cpp/event-handling-in-native-cpp.md) i [obsługi zdarzeń w modelu COM](../cpp/event-handling-in-com.md) dla przykładów.  
  
## <a name="see-also"></a>Zobacz też  
 [Słowa kluczowe](../cpp/keywords-cpp.md)   
 [event_source —](../windows/event-source.md)   
 [event_receiver](../windows/event-receiver.md)   
 [__Event](../cpp/event.md)   
 [__hook](../cpp/hook.md)   
 [__raise](../cpp/raise.md)