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
ms.openlocfilehash: c1c9fa5a6df4cbb1c18e5d5406bdde0197d155b2
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91498819"
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

Słowo kluczowe **`__event`** może być zastosowane do deklaracji metody, deklaracji interfejsu lub deklaracji elementu członkowskiego danych. Nie można jednak użyć **`__event`** słowa kluczowego, aby zakwalifikować element członkowski klasy zagnieżdżonej.

W zależności od tego, czy źródło i odbiorca zdarzenia są natywne C++, COM czy zarządzane (.NET Framework), można użyć następujących konstrukcji jako zdarzeń:

|Natywny język C++|Model COM|Zarządzane (.NET Framework)|
|------------------|---------|--------------------------------|
|Metoda|—|method|
|—|interface|—|
|—|—|element członkowski danych|

Użyj [__hook](../cpp/hook.md) w odbiorniku zdarzenia, aby skojarzyć metodę obsługi z metodą zdarzenia. Należy pamiętać, że po utworzeniu zdarzenia za pomocą **`__event`** słowa kluczowego, wszystkie programy obsługi zdarzeń, które następnie zostały podłączane do tego zdarzenia, będą wywoływane po wywołaniu zdarzenia.

**`__event`** Deklaracja metody nie może mieć definicji; definicja jest generowana niejawnie, więc metodę zdarzenia można wywołać tak, jakby była to metoda zwykła.

> [!NOTE]
> Klasa lub struktura z szablonem nie może zawierać zdarzeń.

## <a name="native-events"></a>Zdarzenia natywne

Zdarzenia natywne to metody. Zwracany typ jest zwykle wartością HRESULT lub **`void`** , ale może być dowolnym typem całkowitym, łącznie z **`enum`** . Gdy zdarzenie używa typu całkowitego powrotu, warunek błędu jest definiowany, gdy program obsługi zdarzeń zwraca wartość różną od zera, w takim przypadku zdarzenie wywoływane wywoła inne Delegaty.

```cpp
// Examples of native C++ events:
__event void OnDblClick();
__event HRESULT OnClick(int* b, char* s);
```

Zobacz [Obsługa zdarzeń w natywnym języku C++](../cpp/event-handling-in-native-cpp.md) dla przykładowego kodu.

## <a name="com-events"></a>Zdarzenia COM

Zdarzenia COM są interfejsami. Parametry metody w interfejsie źródłowym zdarzenia powinny znajdować się *w* parametrach (ale nie jest to rygorystyczne wymuszone), ponieważ parametr *out* nie jest przydatny podczas multiemisji. Jeśli używasz parametru *out* , zostanie wygenerowane ostrzeżenie poziomu 1.

Typ zwracany jest zwykle wartością HRESULT lub **`void`** , ale może być dowolnym typem całkowitym, w tym **`enum`** . Gdy zdarzenie używa całkowitego typu zwracanego, a procedura obsługi zdarzeń zwraca wartość różną od zera, jest to warunek błędu, a w takim przypadku zdarzenie wywoływane przerywa wywołania do innych delegatów. Należy zauważyć, że kompilator automatycznie oznaczy interfejs źródła zdarzeń jako [Źródło](../windows/attributes/source-cpp.md) w wygenerowanym IDL.

Słowo kluczowe [__interface](../cpp/interface.md) jest zawsze wymagane po **`__event`** dla źródła zdarzenia com.

```cpp
// Example of a COM event:
__event __interface IEvent1;
```

Zobacz [Obsługa zdarzeń w modelu COM](../cpp/event-handling-in-com.md) dla przykładowego kodu.

## <a name="managed-events"></a>Zdarzenia zarządzane

Aby uzyskać informacje na temat kodowania zdarzeń w nowej składni, zobacz [Event](../extensions/event-cpp-component-extensions.md).

Zdarzenia zarządzane są elementami członkowskimi lub metodami danych. W przypadku użycia ze zdarzeniem zwracany typ delegata musi być zgodny z [Common Language Specification](/dotnet/standard/language-independence-and-language-independent-components). Zwracany typ procedury obsługi zdarzeń musi być zgodny z typem zwracanym delegata. Aby uzyskać więcej informacji na temat delegatów, zobacz [delegats and Events](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md). Jeśli zarządzanym zdarzeniem jest element członkowski danych, jego typ musi być wskaźnikiem do delegata.

W .NET Framework można traktować składową danych tak, jakby była to sama metoda (czyli `Invoke` Metoda odpowiedniego delegata). Należy wstępnie zdefiniować typ delegata do deklarowania elementu członkowskiego danych zdarzenia zarządzanego. W przeciwieństwie do zarządzanej metody zdarzenia niejawnie definiuje odpowiadającą zarządzaną delegata, jeśli nie jest jeszcze zdefiniowana. Na przykład można zadeklarować wartość zdarzenia, taką jak `OnClick` zdarzenie w następujący sposób:

```cpp
// Examples of managed events:
__event ClickEventHandler* OnClick;  // data member as event
__event void OnClick(String* s);  // method as event
```

Gdy niejawnie deklaruje zdarzenie zarządzane, można określić metody dostępu Add i Remove, które będą wywoływane, gdy programy obsługi zdarzeń zostaną dodane lub usunięte. Można również zdefiniować metodę, która wywołuje (wywołuje) zdarzenie spoza klasy.

## <a name="example-native-events"></a>Przykład: Zdarzenia natywne

```cpp
// EventHandling_Native_Event.cpp
// compile with: /c
[event_source(native)]
class CSource {
public:
   __event void MyEvent(int nValue);
};
```

## <a name="example-com-events"></a>Przykład: zdarzenia COM

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
