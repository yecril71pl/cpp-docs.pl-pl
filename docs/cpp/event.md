---
title: __Event | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- __event_cpp
- __event
dev_langs: C++
helpviewer_keywords:
- __event keyword [C++]
- events [C++], __event
ms.assetid: d3019b3e-722e-48df-8536-c05878461f9e
caps.latest.revision: "14"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4750d156ef4f0f817e1eecec1f4a0842fc229046
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="event"></a>__event
Deklaruje zdarzenie.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      __event   
      method-declarator  
      ;  
__event __interface interface-specifier;  
__event member-declarator;  
```  
  
## <a name="remarks"></a>Uwagi  
 Słowo kluczowe `__event` może odnosić się do deklaracji metody, deklaracji interfejsu lub deklaracji elementu członkowskiego danych. Nie można jednak użyć `__event` — słowo kluczowe na kwalifikować się elementem członkowskim klasy zagnieżdżonej.  
  
 W zależności od tego, czy źródło zdarzenia, a odbiornik natywnych języka C++, COM lub zarządzany (.NET Framework) można użyć jako zdarzenia następujące elementy:  
  
|Natywnych języka C++|Model COM|Zarządzany (.NET Framework)|  
|------------------|---------|--------------------------------|  
|Metoda|—|— metoda|  
|—|interface|—|  
|—|—|element członkowski danych|  
  
 Użyj [__hook](../cpp/hook.md) w odbiorca zdarzenia do skojarzenia z metodą zdarzeń metoda obsługi. Należy pamiętać, że po utworzeniu zdarzenia `__event` — słowo kluczowe, wszystkie programy obsługi zdarzeń, następnie argumentów podłączono do tego zdarzenia zostanie wywołana po wywołaniu zdarzenia.  
  
 `__event` Deklaracja metody nie może mieć definicji; definicji jest generowany niejawnie, tak jak w przypadku dowolnej zwykłej metody można wywołać metody zdarzeń.  
  
> [!NOTE]
>  Szablonu klasy lub struktury nie mogą zawierać zdarzenia.  
  
## <a name="native-events"></a>Natywny zdarzenia  
 Zdarzenia natywnego metodami. Typ zwracany jest zwykle `HRESULT` lub `void`, ale mogą być dowolnego typu całkowitego, łącznie z `enum`. Gdy zdarzenie używa zwracanym typem całkowitym, warunek błędu jest definiowany podczas obsługi zdarzeń zwraca wartość różną od zera, w którym wywoła zdarzeń zgłaszanych przypadku innych obiektów delegowanych.  
  
```  
// Examples of native C++ events:  
__event void OnDblClick();  
__event HRESULT OnClick(int* b, char* s);  
```  
  
 Zobacz [obsługi zdarzeń w natywnym kodzie C++](../cpp/event-handling-in-native-cpp.md) przykładowy kod.  
  
## <a name="com-events"></a>Zdarzenia COM  
 Zdarzenia COM są interfejsy. Parametry metody w interfejsie źródła zdarzeń powinny być **w** parametrów (ale to nie jest wymuszana szczegółowa analiza), ponieważ **limit** parametr nie jest przydatne w przypadku multiemisji. Ostrzeżenia poziomu 1 będą wystawiane, jeśli używasz **limit** parametru.  
  
 Typ zwracany jest zwykle `HRESULT` lub `void`, ale mogą być dowolnego typu całkowitego, łącznie z `enum`. Jeśli zdarzenie używa zwracanym typem całkowitym i program obsługi zdarzeń zwraca wartość niezerową, jest błąd, w których przypadku zdarzeń zgłaszanych przerywa wywołania do innych obiektów delegowanych. Należy pamiętać, kompilator automatycznie oznaczy interfejs źródła zdarzeń jako [źródła](../windows/source-cpp.md) w wygenerowanym pliku IDL.  
  
 [__Interface](../cpp/interface.md) — słowo kluczowe jest zawsze wymagane po `__event` źródła zdarzeń COM.  
  
```  
// Example of a COM event:  
__event __interface IEvent1;  
```  
  
 Zobacz [obsługi zdarzeń w modelu COM](../cpp/event-handling-in-com.md) przykładowy kod.  
  
## <a name="managed-events"></a>Zdarzeń zarządzanych  
 Aby informacji na temat kodowania zdarzeń w nowej składni, zobacz [zdarzeń](../windows/event-cpp-component-extensions.md).  
  
 Zarządzane zdarzenia są elementy członkowskie danych lub metody. W przypadku użycia z zdarzenia, typ zwracany delegata musi być zgodny z [specyfikacja języka wspólnego](/dotnet/standard/language-independence-and-language-independent-components). Zwracany typ obsługi zdarzeń musi odpowiadać zwracanym typem obiektu delegowanego. Aby uzyskać więcej informacji na delegatów, zobacz [delegaci i zdarzenia](../dotnet/delegates-and-events.md). W przypadku zarządzanych zdarzeń jest elementem członkowskim danych, musi być typu wskaźnik do delegata.  
  
 W programie .NET Framework można traktować elementu członkowskiego danych tak, jakby była samej metody (oznacza to, `Invoke` metody swojego delegata odpowiedniego). Typ delegata musi wstępnie deklarowania element danych zarządzanych zdarzeń. Z kolei metody zarządzanych zdarzeń niejawnie definiuje odpowiedniego delegata zarządzanych, jeśli nie jest już zdefiniowany. Na przykład można zadeklarować wartość zdarzenia, takie jak `OnClick` jako zdarzenie w następujący sposób:  
  
```  
// Examples of managed events:  
__event ClickEventHandler* OnClick;  // data member as event  
__event void OnClick(String* s);  // method as event  
```  
  
 Przy deklarowaniu niejawnie zarządzanych zdarzeń, można określić dostępu, które będą wywoływane podczas dodawania lub usuwania programów obsługi zdarzeń add i remove. Istnieje także możliwość zdefiniowania metody, która wywołuje (zgłasza) zdarzenia z poza klasą.  
  
## <a name="example-native-events"></a>Przykład: Native zdarzenia  
  
```  
// EventHandling_Native_Event.cpp  
// compile with: /c  
[event_source(native)]  
class CSource {  
public:  
   __event void MyEvent(int nValue);  
};  
```  
  
## <a name="example-com-events"></a>Przykład: Zdarzeń COM  
  
```  
// EventHandling_COM_Event.cpp  
// compile with: /c  
#define _ATL_ATTRIBUTES 1  
#include <atlbase.h>  
#include <atlcom.h>  
  
[ module(dll, name="EventSource", uuid="6E46B59E-89C3-4c15-A6D8-B8A1CEC98830") ];  
  
[ dual, uuid("00000000-0000-0000-0000-000000000002") ]  
__interface IEventSource {  
   [id(1)] HRESULT MyEvent();  
};  
 [ coclass, uuid("00000000-0000-0000-0000-000000000003"),  event_source(com) ]  
class CSource : public IEventSource {  
public:  
   __event __interface IEventSource;  
   HRESULT FireEvent() {  
      __raise MyEvent();  
      return S_OK;  
   }  
};  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Słowa kluczowe](../cpp/keywords-cpp.md)   
 [Obsługa zdarzeń](../cpp/event-handling.md)   
 [event_source —](../windows/event-source.md)   
 [event_receiver](../windows/event-receiver.md)   
 [__hook](../cpp/hook.md)   
 [__unhook](../cpp/unhook.md)   
 [__raise](../cpp/raise.md)