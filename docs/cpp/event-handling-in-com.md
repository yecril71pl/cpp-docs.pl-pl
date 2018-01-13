---
title: "Obsługa zdarzeń w modelu COM | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- event handling [C++], COM
- event handling [C++], about event handling
- declaring events
- event handlers [C++], COM
- event handlers
- COM, events
- event receivers, in event handling
- event handling [C++]
- hooking events
- event receivers, name and signature matching
- event sources, in event handling
- declaring events, in COM
- declaring events, event handling in COM
ms.assetid: 6b4617d4-a58e-440c-a8a6-1ad1c715b2bb
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1c57b8429a05ab3989dce318f4c16a58475560a1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="event-handling-in-com"></a>Obsługa zdarzeń w modelu COM
W obsłudze zdarzeń COM, konfigurowanie obsługiwanego odbiornika źródła i zdarzeń za pomocą [event_source —](../windows/event-source.md) i [event_receiver](../windows/event-receiver.md) atrybutów, określając `type` = **com**. Te atrybuty wprowadzają odpowiedni kod dla interfejsów niestandardowych, wysyłania i dualnych, aby umożliwić odpowiednim klasom wywoływanie zdarzeń i obsługę zdarzeń za pośrednictwem punktów połączenia COM.  
  
## <a name="declaring-events"></a>Deklarowanie zdarzeń  
 W klasie źródła zdarzeń, użyj [__event](../cpp/event.md) — słowo kluczowe w deklaracji interfejsu, aby zadeklarować metody tego interfejsu jako zdarzenia. Zdarzenia tego interfejsu są uruchamiane podczas wywoływania ich jako metod interfejsu. Metody interfejsów zdarzeń może mieć zero lub więcej parametrów (który powinny być **w** parametrów). Zwracany typ może być typu void lub dowolnego całkowitego.  
  
## <a name="defining-event-handlers"></a>Definiowanie programów obsługi zdarzeń  
 W klasie odbiornika zdarzeń należy zdefiniować programy obsługi zdarzeń, które są metodami z podpisami (typy zwracane, konwencje wywoływania i argumenty), które odpowiadają obsługiwanemu zdarzeniu. Dla zdarzeń COM konwencji wywoływania nie musi odpowiadać; zobacz [układu zależnych zdarzeń COM](#vcconeventhandlingincomanchorlayoutdependentcomevents) poniżej szczegółowe informacje.  
  
## <a name="hooking-event-handlers-to-events"></a>Podłączanie programów obsługi zdarzeń do zdarzeń  
 Również w klasy odbiorcy zdarzeń, można używać funkcji wewnętrznej [__hook](../cpp/hook.md) do skojarzenia zdarzeń z obsługi zdarzeń i [__unhook](../cpp/unhook.md) można usunąć skojarzenia zdarzenia z obsługi zdarzeń. Można podłączyć kilka zdarzeń do programu obsługi zdarzeń lub kilka programów obsługi zdarzeń do zdarzenia.  
  
> [!NOTE]
>  Zwykle istnieją dwie techniki udostępniające odbiorcy zdarzenia COM definicje interfejsu źródła zdarzeń. Pierwszą techniką, jak pokazano poniżej, jest udostępnienie wspólnego pliku nagłówkowego. Druga to użycie [#import](../preprocessor/hash-import-directive-cpp.md) z `embedded_idl` zaimportować kwalifikator, dzięki czemu biblioteki typów źródła zdarzenia są zapisywane do pliku danych .tlh — kod wygenerowany przez atrybut zachowane.  
  
## <a name="firing-events"></a>Wyzwalanie zdarzeń  
 Aby wyzwolić zdarzenie, po prostu wywołaj metodę w zadeklarowanym interfejsie za pomocą słowa kluczowego `__event` w klasie źródła zdarzenia. Jeśli programy obsługi zostały podłączone do zdarzenia, zostaną wywołane programy obsługi.  
  
### <a name="com-event-code"></a>Kod zdarzenia COM  
 Poniższy przykład pokazuje jak wywołać zdarzenie w klasie COM. Aby skompilować i uruchomić przykład, zobacz komentarze w kodzie.  
  
```  
// evh_server.h  
#pragma once  
  
[ dual, uuid("00000000-0000-0000-0000-000000000001") ]  
__interface IEvents {  
   [id(1)] HRESULT MyEvent([in] int value);  
};  
  
[ dual, uuid("00000000-0000-0000-0000-000000000002") ]  
__interface IEventSource {  
   [id(1)] HRESULT FireEvent();  
};  
  
class DECLSPEC_UUID("530DF3AD-6936-3214-A83B-27B63C7997C4") CSource;  
```  
  
 A następnie serwera:  
  
```  
// evh_server.cpp  
// compile with: /LD  
// post-build command: Regsvr32.exe /s evh_server.dll  
#define _ATL_ATTRIBUTES 1  
#include <atlbase.h>  
#include <atlcom.h>  
#include "evh_server.h"  
  
[ module(dll, name="EventSource", uuid="6E46B59E-89C3-4c15-A6D8-B8A1CEC98830") ];  
  
[coclass, event_source(com), uuid("530DF3AD-6936-3214-A83B-27B63C7997C4")]  
class CSource : public IEventSource {  
public:  
   __event __interface IEvents;   
  
   HRESULT FireEvent() {  
      __raise MyEvent(123);  
      return S_OK;  
   }  
};  
```  
  
 A następnie klienta:  
  
```  
// evh_client.cpp  
// compile with: /link /OPT:NOREF  
#define _ATL_ATTRIBUTES 1  
#include <atlbase.h>  
#include <atlcom.h>  
#include <stdio.h>  
#include "evh_server.h"  
  
[ module(name="EventReceiver") ];  
  
[ event_receiver(com) ]  
class CReceiver {  
public:  
   HRESULT MyHandler1(int nValue) {  
      printf_s("MyHandler1 was called with value %d.\n", nValue);  
      return S_OK;  
   }  
  
   HRESULT MyHandler2(int nValue) {  
      printf_s("MyHandler2 was called with value %d.\n", nValue);  
      return S_OK;  
   }  
  
   void HookEvent(IEventSource* pSource) {  
      __hook(&IEvents::MyEvent, pSource, &CReceiver::MyHandler1);  
      __hook(&IEvents::MyEvent, pSource, &CReceiver::MyHandler2);  
   }  
  
   void UnhookEvent(IEventSource* pSource) {  
      __unhook(&IEvents::MyEvent, pSource, &CReceiver::MyHandler1);  
      __unhook(&IEvents::MyEvent, pSource, &CReceiver::MyHandler2);  
   }  
};  
  
int main() {  
   // Create COM object  
   CoInitialize(NULL);  
   {  
      IEventSource* pSource = 0;  
      HRESULT hr = CoCreateInstance(__uuidof(CSource), NULL,         CLSCTX_ALL, __uuidof(IEventSource), (void **) &pSource);  
      if (FAILED(hr)) {  
         return -1;  
      }  
  
      // Create receiver and fire event  
      CReceiver receiver;  
      receiver.HookEvent(pSource);  
      pSource->FireEvent();  
      receiver.UnhookEvent(pSource);  
   }  
   CoUninitialize();  
   return 0;  
}  
```  
  
### <a name="output"></a>Dane wyjściowe  
  
```  
MyHandler1 was called with value 123.  
MyHandler2 was called with value 123.  
```  
  
##  <a name="vcconeventhandlingincomanchorlayoutdependentcomevents"></a>Zdarzenia COM zależnych układu  
 Zależność układu jest tylko problemem programowania COM. W obsłudze zdarzeń macierzystych i zarządzanych, podpisy (typy zwracane, konwencja wywoływania i argumenty) z programów obsługi muszą odpowiadać ich zdarzeniom, ale nazwy programów obsługi nie muszą odpowiadać ich zdarzeniom.  
  
 Jednak w obsłudze zdarzeń COM, gdy ustawisz *layout_dependent* parametr **event_receiver** do **true**, zgodność nazwy i podpisu jest wymuszana. Oznacza to, że nazwy i wzory podpisów w programach obsługi zdarzeń muszą dokładnie odpowiadać nazwom i wzorom podpisów zdarzeń, do których są podłączone.  
  
 Gdy *layout_dependent* ma ustawioną wartość **false**, wywoływania klasy Konwencji i magazynu (wirtualny, statyczne i itd.) może być mieszany i dopasować między uruchamiania metody zdarzeń oraz hooking metod (jego Obiekty delegowane). Nieco bardziej wydajny mają *layout_dependent*=**true**.  
  
 Załóżmy, że `IEventSource` jest zdefiniowany dla następujących metod:  
  
```  
[id(1)] HRESULT MyEvent1([in] int value);  
[id(2)] HRESULT MyEvent2([in] int value);  
```  
  
 Przyjęto założenie, że źródło zdarzenia ma następującą postać:  
  
```  
[coclass, event_source(com)]  
class CSource : public IEventSource {  
public:  
   __event __interface IEvents;  
  
   HRESULT FireEvent() {  
      MyEvent1(123);  
      MyEvent2(123);  
      return S_OK;  
   }  
};  
```  
  
 Następnie, w przypadku odbiornika, każdy program obsługi podłączony do metody w `IEventSource` musi odpowiadać jej nazwie i podpisie, w następujący sposób:  
  
```  
[coclass, event_receiver(com, true)]  
class CReceiver {  
public:  
   HRESULT MyEvent1(int nValue) {  // name and signature matches MyEvent1  
      ...  
   }  
   HRESULT MyEvent2(E c, char* pc) {  // signature doesn't match MyEvent2  
      ...  
   }  
   HRESULT MyHandler1(int nValue) {  // name doesn't match MyEvent1 (or 2)  
      ...  
   }  
   void HookEvent(IEventSource* pSource) {  
      __hook(IFace, pSource);  // Hooks up all name-matched events   
                               // under layout_dependent = true  
      __hook(&IFace::MyEvent1, pSource, &CReceive::MyEvent1);   // valid  
      __hook(&IFace::MyEvent2, pSource, &CSink::MyEvent2);   // not valid  
      __hook(&IFace::MyEvent1, pSource, &CSink:: MyHandler1); // not valid  
   }  
};  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa zdarzeń](../cpp/event-handling.md)