---
title: __event
ms.date: 11/04/2016
f1_keywords:
- __event_cpp
- __event
helpviewer_keywords:
- __event keyword [C++]
- events [C++], __event
ms.assetid: d3019b3e-722e-48df-8536-c05878461f9e
ms.openlocfilehash: f8935408c6e9b43347d4ad6088505a461e254ae2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366305"
---
# <a name="__event"></a>__event

Deklaruje zdarzenie.

## <a name="syntax"></a>Składnia

```
__event method-declarator;
__event __interface interface-specifier;
__event member-declarator;
```

## <a name="remarks"></a>Uwagi

**__event** słowa kluczowego można zastosować do deklaracji metody, deklaracji interfejsu lub deklaracji elementu członkowskiego danych. Jednak nie można użyć **__event** słowa kluczowego, aby zakwalifikować członka klasy zagnieżdżonej.

W zależności od tego, czy źródło zdarzeń i odbiorca są natywne C++, COM lub zarządzane (.NET Framework), można użyć następujących konstrukcji jako zdarzeń:

|Natywny język C++|Model COM|Zarządzane (.NET Framework)|
|------------------|---------|--------------------------------|
|Metoda|—|method|
|—|interface|—|
|—|—|element członkowski danych|

Użyj [__hook](../cpp/hook.md) w odbiorniku zdarzeń, aby skojarzyć metodę obsługi z metodą zdarzenia. Należy zauważyć, że po utworzeniu zdarzenia z **__event** słowa kluczowego wszystkie programy obsługi zdarzeń następnie podłączone do tego zdarzenia zostaną wywołane, gdy zdarzenie zostanie wywołane.

Deklaracja metody **__event** nie może mieć definicji; definicja jest niejawnie generowane, więc metoda zdarzenia można wywołać tak, jakby była to zwykła metoda.

> [!NOTE]
> Klasa szablonu lub struktura nie może zawierać zdarzeń.

## <a name="native-events"></a>Zdarzenia natywne

Zdarzenia natywne są metodami. Typ zwracany jest zazwyczaj HRESULT lub **void**, ale może być dowolny typ integralny, w tym **wyliczenia.** Gdy zdarzenie używa typu powrotu integralną, warunek błędu jest definiowany, gdy program obsługi zdarzeń zwraca wartość niezerową, w którym to przypadku wywoływane zdarzenie wywoła innych delegatów.

```cpp
// Examples of native C++ events:
__event void OnDblClick();
__event HRESULT OnClick(int* b, char* s);
```

Zobacz [obsługa zdarzeń w natywnym języku C++](../cpp/event-handling-in-native-cpp.md) dla przykładowego kodu.

## <a name="com-events"></a>Zdarzenia COM

Zdarzenia COM są interfejsami. Parametry metody w interfejsie źródła zdarzeń powinny być *w* parametrach (ale nie jest to rygorystycznie wymuszane), ponieważ *out* parametr nie jest przydatne podczas multiemisji. Ostrzeżenie poziomu 1 zostanie wydane, jeśli użyjesz parametru *out.*

Typ zwracany jest zazwyczaj HRESULT lub **void**, ale może być dowolny typ integralny, w tym **wyliczenia.** Gdy zdarzenie używa typu powrotu integralną i program obsługi zdarzeń zwraca wartość niezerową, jest to warunek błędu, w którym to przypadku zdarzenie wywoływane przerywa wywołania do innych delegatów. Należy zauważyć, że kompilator automatycznie oznaczy interfejs źródła zdarzeń jako [źródło](../windows/attributes/source-cpp.md) w wygenerowanym IDL.

[__interface](../cpp/interface.md) słowo kluczowe jest zawsze wymagane po **__event** dla źródła zdarzeń COM.

```cpp
// Example of a COM event:
__event __interface IEvent1;
```

Zobacz [obsługa zdarzeń w COM](../cpp/event-handling-in-com.md) dla przykładowego kodu.

## <a name="managed-events"></a>Zdarzenia zarządzane

Aby uzyskać informacje na temat kodowania zdarzeń w nowej składni, zobacz [zdarzenie](../extensions/event-cpp-component-extensions.md).

Zdarzenia zarządzane są elementy członkowskie danych lub metody. W przypadku użycia ze zdarzeniem typ zwracany pełnomocnika musi być zgodny ze [specyfikacją języka wspólnego](/dotnet/standard/language-independence-and-language-independent-components). Zwracany typ programu obsługi zdarzeń musi być zgodny z typem zwracanego pełnomocnika. Aby uzyskać więcej informacji na temat delegatów, zobacz [Pełnomocnicy i wydarzenia](../dotnet/delegates-and-events.md). Jeśli zdarzenie zarządzane jest elementem członkowskim danych, jego typ musi być wskaźnikiem do pełnomocnika.

W .NET Framework można traktować element członkowski danych tak, jakby była `Invoke` to sama metoda (czyli metoda jego odpowiedniego delegata). Należy wstępnie zdefiniować typ delegata do deklarowania elementu członkowskiego danych zdarzenia zarządzanego. Natomiast metoda zdarzenia zarządzanego niejawnie definiuje odpowiedni zarządzany delegat, jeśli nie jest jeszcze zdefiniowany. Na przykład można zadeklarować wartość `OnClick` zdarzenia, takie jak zdarzenie, w następujący sposób:

```cpp
// Examples of managed events:
__event ClickEventHandler* OnClick;  // data member as event
__event void OnClick(String* s);  // method as event
```

Podczas niejawnego deklarowania zdarzenia zarządzanego, można określić dodać i usunąć akcesory, które będą wywoływane podczas obsługi zdarzeń są dodawane lub usuwane. Można również zdefiniować metodę, która wywołuje (wywołuje) zdarzenie spoza klasy.

## <a name="example-native-events"></a>Przykład: Zdarzenia macierzyste

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

## <a name="see-also"></a>Zobacz też

[Słowa kluczowe](../cpp/keywords-cpp.md)<br/>
[Obsługa zdarzeń](../cpp/event-handling.md)<br/>
[event_source](../windows/attributes/event-source.md)<br/>
[event_receiver](../windows/attributes/event-receiver.md)<br/>
[__hook](../cpp/hook.md)<br/>
[__unhook](../cpp/unhook.md)<br/>
[__raise](../cpp/raise.md)
