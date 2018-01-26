---
title: "Obsługa zdarzeń w natywnym kodzie C++ | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords: event handling [C++], Visual C++
ms.assetid: e4b9219a-15d8-42fb-83c8-6d2e4e087c8d
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 157b31f244ce5400aac5857f2473deb67938d8d0
ms.sourcegitcommit: 9a0a287d6940591523af959ebdac5affa36220da
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2018
---
# <a name="event-handling-in-native-c"></a>Obsługa zdarzeń w natywnym kodzie C++

W obsłudze zdarzeń natywnych języka C++, konfigurowanie obsługiwanego odbiornika źródła i zdarzeń za pomocą [event_source —](../windows/event-source.md) i [event_receiver](../windows/event-receiver.md) atrybutów, określając `type` = `native`. Te atrybuty Zezwalaj klasy, do których są stosowane do wyzwalać zdarzeń i obsługa zdarzeń w kontekście macierzystego, -COM.

## <a name="declaring-events"></a>Deklarowanie zdarzeń

W klasie źródła zdarzeń, użyj [__event](../cpp/event.md) — słowo kluczowe w deklaracji metody, aby zadeklarować metodę jako zdarzenie. Upewnij się zadeklarować metodę, ale nie definiują Aby to zrobić wygeneruje błąd kompilatora, ponieważ kompilator definiuje niejawnie metodę, jeśli są wysyłane do zdarzenia. Zdarzenia natywnych może być metody z parametrami zero lub więcej. Zwracany typ może być typu void lub dowolnego całkowitego.  
  
## <a name="defining-event-handlers"></a>Definiowanie programów obsługi zdarzeń

W klasie odbiornika zdarzeń należy zdefiniować programy obsługi zdarzeń, które są metodami z podpisami (typy zwracane, konwencje wywoływania i argumenty), które odpowiadają obsługiwanemu zdarzeniu.  
  
## <a name="hooking-event-handlers-to-events"></a>Podłączanie programów obsługi zdarzeń do zdarzeń  

Również w klasy odbiorcy zdarzeń, można używać funkcji wewnętrznej [__hook](../cpp/hook.md) do skojarzenia zdarzeń z obsługi zdarzeń i [__unhook](../cpp/unhook.md) można usunąć skojarzenia zdarzenia z obsługi zdarzeń. Można podłączyć kilka zdarzeń do programu obsługi zdarzeń lub kilka programów obsługi zdarzeń do zdarzenia.  
  
## <a name="firing-events"></a>Wyzwalanie zdarzeń  

Zdarzenia, po prostu Wywołaj metodę zadeklarowany jako zdarzenie w przypadku klasy źródłowej. Jeśli programy obsługi zostały podłączone do zdarzenia, zostaną wywołane programy obsługi.  
  
### <a name="native-c-event-code"></a>Kod natywny zdarzenia C++  

Poniższy przykład pokazuje, jak zdarzenia w natywnym kodzie C++. Aby skompilować i uruchomić przykład, zobacz komentarze w kodzie.  
  
## <a name="example"></a>Przykład  
  
### <a name="code"></a>Kod  
  
```cpp  
// evh_native.cpp  
#include <stdio.h>  
  
[event_source(native)]  
class CSource {  
public:  
   __event void MyEvent(int nValue);  
};  
  
[event_receiver(native)]  
class CReceiver {  
public:  
   void MyHandler1(int nValue) {  
      printf_s("MyHandler1 was called with value %d.\n", nValue);  
   }  
  
   void MyHandler2(int nValue) {  
      printf_s("MyHandler2 was called with value %d.\n", nValue);  
   }  
  
   void hookEvent(CSource* pSource) {  
      __hook(&CSource::MyEvent, pSource, &CReceiver::MyHandler1);  
      __hook(&CSource::MyEvent, pSource, &CReceiver::MyHandler2);  
   }  
  
   void unhookEvent(CSource* pSource) {  
      __unhook(&CSource::MyEvent, pSource, &CReceiver::MyHandler1);  
      __unhook(&CSource::MyEvent, pSource, &CReceiver::MyHandler2);  
   }  
};  
  
int main() {  
   CSource source;  
   CReceiver receiver;  
  
   receiver.hookEvent(&source);  
   __raise source.MyEvent(123);  
   receiver.unhookEvent(&source);  
}  
```  
  
### <a name="output"></a>Dane wyjściowe  
  
```Output
MyHandler2 was called with value 123.  
MyHandler1 was called with value 123.  
```  
  
## <a name="see-also"></a>Zobacz też

[Obsługa zdarzeń](../cpp/event-handling.md)  

