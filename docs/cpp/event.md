---
title: __Event | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- __event_cpp
- __event
dev_langs:
- C++
helpviewer_keywords:
- __event keyword [C++]
- events [C++], __event
ms.assetid: d3019b3e-722e-48df-8536-c05878461f9e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 74b79edb24396896a6c8a50965081e9466720ca4
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/01/2018
ms.locfileid: "39407828"
---
# <a name="event"></a>__event
Deklaruje zdarzenie.  
  
## <a name="syntax"></a>Składnia  
  
```  
__event method-declarator;  
__event __interface interface-specifier;  
__event member-declarator;  
```  
  
## <a name="remarks"></a>Uwagi  
 Słowo kluczowe **__event** można zastosować do deklaracji metody, deklaracji interfejsu lub deklaracja składowej danych. Nie można jednak użyć **__event** — słowo kluczowe, aby zakwalifikować składową klasy zagnieżdżone.  
  
 W zależności od tego, czy Twoje źródło zdarzeń i odbiorcy są natywnych języka C++, COM lub zarządzany (.NET Framework) następujące konstrukcje służy jako zdarzenia:  
  
|Natywnych języka C++|Model COM|Zarządzany (.NET Framework)|  
|------------------|---------|--------------------------------|  
|Metoda|—|— metoda|  
|—|interface|—|  
|—|—|element członkowski danych|  
  
 Użyj [__hook](../cpp/hook.md) w odbiorcy zdarzeń, aby skojarzyć metodę programu obsługi z metodę zdarzeń. Należy pamiętać, że po utworzeniu zdarzenia o **__event** — słowo kluczowe, wszystkich procedur obsługi zdarzeń, następnie jest podłączone do tego zdarzenia będzie wywoływany, gdy zdarzenie jest wywoływane.  
  
 **__Event** deklaracji metody nie może mieć definicji; definicja jest generowane niejawnie, tak jak w przypadku dowolnej zwykłej metody można wywołać metody zdarzeń.  
  
> [!NOTE]
>  Szablonem klasy lub struktury nie mogą zawierać zdarzenia.  
  
## <a name="native-events"></a>Macierzystych zdarzeń  
 Macierzystych zdarzeń są metodami. Typ zwracany jest zazwyczaj HRESULT lub **void**, ale może być dowolnym typem integralnym, w tym **wyliczenia**. Gdy zdarzenie używa zwracanym typem całkowitym, warunek błędu definiuje się program obsługi zdarzeń, zwraca wartość różną od zera, w którym będzie wywoływać przypadków dla wywoływanego zdarzenia innych obiektów delegowanych.  
  
```cpp 
// Examples of native C++ events:  
__event void OnDblClick();  
__event HRESULT OnClick(int* b, char* s);  
```  
  
 Zobacz [zdarzenie obsługi w natywnym kodzie C++](../cpp/event-handling-in-native-cpp.md) przykładowy kod.  
  
## <a name="com-events"></a>Zdarzenia COM  
 Zdarzenia COM to interfejsy. Parametry metody w interfejsie źródła zdarzeń powinny być *w* parametrów (ale nie jest to wymuszane rygorystycznie), ponieważ *się* parametr jest przydatne, gdy multiemisji. Ostrzeżenia poziomu 1 będą wystawiane, jeśli używasz *się* parametru.  
  
 Typ zwracany jest zazwyczaj HRESULT lub **void**, ale może być dowolnym typem integralnym, w tym **wyliczenia**. Gdy zdarzenie używa zwracanym typem całkowitym i program obsługi zdarzeń zwraca wartość różną od zera, jest warunkiem błędu, w których przypadku dla wywoływanego zdarzenia przerywa wywołań do innych obiektów delegowanych. Należy pamiętać, kompilator automatycznie oznaczy interfejsu źródła zdarzeń jako [źródła](../windows/source-cpp.md) w wygenerowanym pliku IDL.  
  
 [__Interface](../cpp/interface.md) — słowo kluczowe jest zawsze wymagana po **__event** dla źródła zdarzenia COM.  
  
```cpp 
// Example of a COM event:  
__event __interface IEvent1;  
```  
  
 Zobacz [zdarzenie obsługi w modelu COM](../cpp/event-handling-in-com.md) przykładowy kod.  
  
## <a name="managed-events"></a>Zdarzenia zarządzane  
 Aby uzyskać informacji na temat kodowania zdarzenia w nowej składni, zobacz [zdarzeń](../windows/event-cpp-component-extensions.md).  
  
 Zdarzenia zarządzane są elementy członkowskie danych lub metody. W przypadku użycia ze zdarzeniem, zwracany typ delegata muszą być zgodne z [specyfikacja Common Language Specification](/dotnet/standard/language-independence-and-language-independent-components). Zwracany typ procedury obsługi zdarzeń musi odpowiadać zwracany typ delegata. Aby uzyskać więcej informacji na temat obiektów delegowanych, zobacz [delegaci i zdarzenia](../dotnet/delegates-and-events.md). Jeśli zdarzenie zarządzane jest element członkowski danych, jego typ musi być wskaźnikiem do delegata.  
  
 W .NET Framework, można traktować element członkowski danych, tak jakby sama metoda (czyli `Invoke` metoda jego odpowiedniego delegata). Do deklarowania element członkowski danych zdarzenie zarządzane, należy wstępnie typ delegata. Z kolei metoda zdarzenie zarządzane niejawnie definiuje odpowiedniego zarządzanego obiektu delegowanego, jeśli nie jest już zdefiniowany. Na przykład, można zadeklarować wartość zdarzenia, takie jak `OnClick` jako zdarzenie w następujący sposób:  
  
```cpp 
// Examples of managed events:  
__event ClickEventHandler* OnClick;  // data member as event  
__event void OnClick(String* s);  // method as event  
```  
  
 Podczas deklarowania niejawnie zdarzenie zarządzane, można określić dostępu, które będą wywoływane podczas obsługi zdarzeń są dodawane lub usuwane add i remove. Można również zdefiniować metodę, która wywołuje (generuje) zdarzenie z poza klasy.  
  
## <a name="example-native-events"></a>Przykład: Macierzystych zdarzeń  
  
```cpp 
// EventHandling_Native_Event.cpp  
// compile with: /c  
[event_source(native)]  
class CSource {  
public:  
   __event void MyEvent(int nValue);  
};  
```  
  
## <a name="example-com-events"></a>Przykład: Zdarzenia COM  
  
```cpp 
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
  
## <a name="see-also"></a>Zobacz także  
 [Keywords](../cpp/keywords-cpp.md)   
 [Obsługa zdarzeń](../cpp/event-handling.md)   
 [event_source](../windows/event-source.md)   
 [event_receiver](../windows/event-receiver.md)   
 [__hook](../cpp/hook.md)   
 [__unhook](../cpp/unhook.md)   
 [__raise](../cpp/raise.md)