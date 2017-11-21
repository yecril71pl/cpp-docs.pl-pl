---
title: __hook | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: __hook_cpp
dev_langs: C++
helpviewer_keywords:
- __hook keyword [C++]
- event handlers [C++], connecting events to
ms.assetid: f4cabb10-d293-4c0e-a1d2-4745ef9cc22c
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 98a18a7e145a2b23b13e38bd07d5b29c5a397d6f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="hook"></a>__hook
Kojarzy metoda obsługi ze zdarzeniem.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      long __hook(  
   &SourceClass::EventMethod,  
   source,  
   &ReceiverClass::HandlerMethod  
   [, receiver = this]  
);  
long __hook(  
   interface,  
   source  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 **&***SourceClass* `::` *EventMethod*  
 Wskaźnik do metody zdarzeń, do którego zostanie utworzenie punktu zaczepienia metoda obsługi zdarzeń:  
  
-   Natywny zdarzenia C++: *SourceClass* jest klasa źródła zdarzeń i *EventMethod* jest zdarzenie.  
  
-   Zdarzenia COM: *SourceClass* jest interfejsem źródła zdarzeń i *EventMethod* jest jedną z metod.  
  
-   Zarządzanych zdarzeń: *SourceClass* jest klasa źródła zdarzeń i *EventMethod* jest zdarzenie.  
  
 `interface`  
 Nazwa interfejsu, jest powiązana z `receiver`, tylko dla odbiorcy zdarzeń COM, w którym *layout_dependent* parametr [event_receiver](../windows/event-receiver.md) atrybutu **true**.  
  
 *źródło*  
 Wskaźnik do wystąpienia źródła zdarzenia. W zależności od kodu `type` określony w **event_receiver**, *źródła* może być jedną z następujących czynności:  
  
-   Wskaźnik obiektu źródła zdarzeń macierzystego.  
  
-   **IUnknown**— na podstawie wskaźnika (COM źródła).  
  
-   Wskaźnik zarządzanego obiektu (w przypadku zarządzanych zdarzeń).  
  
 **&***ReceiverClass* `::``HandlerMethod`  
 Wskaźnik do metoda obsługi zdarzeń, aby być dołączane do zdarzeń. Program obsługi jest określony jako metody klasy lub odwołanie do tego samego; Jeśli nie określisz nazwy klasy `__hook` zakłada klasy się, że w którym jest wywoływana.  
  
-   Natywny zdarzenia C++: *ReceiverClass* jest klasy odbiorcy zdarzeń i `HandlerMethod` jest programem obsługi.  
  
-   Zdarzenia COM: *ReceiverClass* jest interfejsem odbiorcy zdarzeń i `HandlerMethod` jest jednym z jego obsługi.  
  
-   Zarządzanych zdarzeń: *ReceiverClass* jest klasy odbiorcy zdarzeń i `HandlerMethod` jest programem obsługi.  
  
 `receiver`(opcjonalnie)  
 Wskaźnik do wystąpienia klasy odbiorcy zdarzeń. Jeśli odbiornik nie zostanie określony, wartością domyślną jest odbiornik klasy lub struktury, w którym `__hook` jest wywoływana.  
  
## <a name="usage"></a>Użycie  
 Może być używany w żadnych zakresu funkcji, w tym głównym poza klasy odbiorcy zdarzeń.  
  
## <a name="remarks"></a>Uwagi  
 Użyj funkcji wewnętrznej `__hook` w odbiornik zdarzeń, aby skojarzyć lub utworzenie punktu zaczepienia metody obsługi z metoda zdarzeń. Określona Obsługa następnie jest wywoływane, gdy źródło uruchamia określone zdarzenie. Zostanie utworzenie punktu zaczepienia kilka obsługi do jednego zdarzenia lub utworzenie punktu zaczepienia kilka zdarzeń do pojedynczego programu obsługi.  
  
 Istnieją dwie formy `__hook`. Użyj pierwszego formularza (cztery argument) w większości przypadków, w szczególności dla odbiorcy zdarzeń COM, w którym *layout_dependent* parametr [event_receiver](../windows/event-receiver.md) atrybutu **false** .  
  
 W takich przypadkach jest konieczne utworzenie punktu zaczepienia wszystkie metody w interfejsie, zanim zostanie zainicjowane zdarzenie na jednej z metod; Metoda obsługi zdarzeń musi być punktem zaczepienia. Można użyć drugiej formy (dwuargumentowej) `__hook` tylko dla odbiorcy zdarzeń COM, w którym *layout_dependent***= true**.  
  
 `__hook`Zwraca wartość typu long. Podano niezerowe wartości zwracanej wskazuje wystąpił błąd (Zgłoś wyjątek zarządzanych zdarzeń).  
  
 Kompilator sprawdza istnienie zdarzeń oraz że z sygnaturą zdarzenia zgadza się z podpisu delegata.  
  
 Z wyjątkiem zdarzeń COM `__hook` i `__unhook` może być wywołana poza odbiorcy zdarzeń.  
  
 Zamiast `__hook` jest użycie += — operator.  
  
 Aby uzyskać informacji na temat kodowania zarządzanych zdarzeń w nowej składni, zobacz [zdarzeń](../windows/event-cpp-component-extensions.md).  
  
> [!NOTE]
>  Szablonu klasy lub struktury nie mogą zawierać zdarzenia.  
  
## <a name="example"></a>Przykład  
 Zobacz [obsługi zdarzeń w natywnym kodzie C++](../cpp/event-handling-in-native-cpp.md) i [obsługi zdarzeń w modelu COM](../cpp/event-handling-in-com.md) dla przykładów.  
  
## <a name="see-also"></a>Zobacz też  
 [Słowa kluczowe](../cpp/keywords-cpp.md)   
 [Obsługa zdarzeń](../cpp/event-handling.md)   
 [event_source —](../windows/event-source.md)   
 [event_receiver](../windows/event-receiver.md)   
 [__unhook](../cpp/unhook.md)   
 [__raise](../cpp/raise.md)