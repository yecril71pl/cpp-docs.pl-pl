---
title: Event (C++ Component Extensions) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event
- event_cpp
dev_langs:
- C++
helpviewer_keywords:
- event keyword [C++]
ms.assetid: c4998e42-883c-4419-bbf4-36cdc979dd27
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f001f61a9425a064d3b899beb6cbb689471da5bf
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46442594"
---
# <a name="event--c-component-extensions"></a>event (C++ Component Extensions)

**Zdarzeń** deklaruje — słowo kluczowe *zdarzeń*, czyli powiadomienia do subskrybentów zarejestrowany (*procedury obsługi zdarzeń*) która jest przeprowadzana w stanie się coś istotnego.

## <a name="all-runtimes"></a>Wszystkie środowiska wykonawcze

C + +/ CX obsługuje deklarowania *składowej zdarzenia* lub *bloku zdarzeń*. Element członkowski zdarzenia jest skrótem do deklarowania bloku zdarzeń. Domyślnie deklaruje element członkowski zdarzenia `add()`, `remove()`, i `raise()` funkcje, które są jawnie zadeklarowane w bloku zdarzeń. Aby dostosować funkcje w element członkowski zdarzenia, zamiast deklarowania bloku zdarzeń, a następnie zastąpić funkcje, których potrzebujesz.

### <a name="syntax"></a>Składnia

```cpp
// event data member
modifiereventdelegate^ event_name;

// event block
modifiereventdelegate^ event_name
{
   modifierreturn_valueadd(delegate^ name);
   modifier void remove(delegate^ name);
   modifier void raise(parameters);
}
```

### <a name="parameters"></a>Parametry

*Modyfikator*<br/>
Modyfikatory, które mogą być używane w zgłoszeniu zdarzenia lub metody dostępu zdarzeń.  Możliwe wartości to **statyczne** i **wirtualnego**.

*delegate*<br/>
[Delegować](../windows/delegate-cpp-component-extensions.md), którego podpis programu obsługi zdarzeń muszą być zgodne.

*nazwa_zdarzenia*<br/>
Nazwa zdarzenia.

*wartość_zwracana*<br/>
Wartość zwracaną metody dostępu zdarzeń.  Jako możliwe do zweryfikowania, zwracanym typem musi być **void**.

*Parametry*<br/>
(opcjonalnie) Parametry `raise` metody, która pasuje do podpisu z *delegować* parametru.

### <a name="remarks"></a>Uwagi

Zdarzenie jest skojarzenie między delegata, a funkcja członkowska (program obsługi zdarzeń), która odpowiada wyzwolenie zdarzenia i umożliwia klientom z dowolnej klasy do zarejestrowania metod, które są zgodne z podpis i zwracany typ delegata bazowego.

Istnieją dwa rodzaje zdarzeń deklaracje:

*element członkowski danych zdarzeń*<br/>
Kompilator automatycznie tworzy magazynu dla zdarzenia w postaci elementu członkowskiego typu delegata i tworzy wewnętrzny `add()`, `remove()`, i `raise()` funkcji elementów członkowskich. Element członkowski danych zdarzenia muszą być zadeklarowane wewnątrz klasy. Zwracany typ zwracany typ obiektu delegowanego musi odpowiadać zwracanym typem obsługi zdarzeń.

*bloku zdarzeń*<br/>
Blok zdarzeń umożliwia jawnie zadeklarować i dostosowywanie zachowania `add()`, `remove()`, i `raise()` metody.

Możesz użyć **+= operatory** i **operator-=** do dodawania i usuwania zdarzenia obsługi lub wywołanie `add()` i `remove()` metody jawnie.

**Zdarzenie** jest kontekstowe słowo kluczowe; zobacz [Context-Sensitive Keywords](../windows/context-sensitive-keywords-cpp-component-extensions.md) Aby uzyskać więcej informacji.

## <a name="windows-runtime"></a>Środowisko wykonawcze systemu Windows

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [zdarzenia (C + +/ CX)](https://msdn.microsoft.com/library/windows/apps/hh755799.aspx).

Jeśli zamierzasz dodać, a następnie usuń procedurę obsługi zdarzeń, musisz najpierw zapisać struktury EventRegistrationToken, który jest zwracany przez operacji dodawania. Następnie w operacji usuwania, należy użyć zapisanych struktury EventRegistrationToken do identyfikowania programu obsługi zdarzeń do usunięcia.

### <a name="requirements"></a>Wymagania

— Opcja kompilatora: `/ZW`

## <a name="common-language-runtime"></a>środowiska uruchomieniowe w trakcie wykonania

**Zdarzeń** — słowo kluczowe pozwala zadeklarować zdarzenia. Zdarzenie jest się dzieje w sposób, aby klasa zapewniała powiadomienia, gdy coś w zainteresowania.

### <a name="syntax"></a>Składnia

```cpp
// event data member
modifiereventdelegate^ event_name;

// event block
modifiereventdelegate^ event_name
{
   modifierreturn_valueadd(delegate^ name);
   modifier void remove(delegate^ name);
   modifier void raise(parameters);
}
```

### <a name="parameters"></a>Parametry

*Modyfikator*<br/>
Modyfikatory, które mogą być używane w zgłoszeniu zdarzenia lub metody dostępu zdarzeń.  Możliwe wartości to **statyczne** i **wirtualnego**.

*delegate*<br/>
[Delegować](../windows/delegate-cpp-component-extensions.md), którego podpis programu obsługi zdarzeń muszą być zgodne.

*nazwa_zdarzenia*<br/>
Nazwa zdarzenia.

*wartość_zwracana*<br/>
Wartość zwracaną metody dostępu zdarzeń.  Jako możliwe do zweryfikowania, zwracanym typem musi być **void**.

*Parametry*<br/>
(opcjonalnie) Parametry `raise` metody, która pasuje do podpisu z *delegować* parametru.

### <a name="remarks"></a>Uwagi

Zdarzenie jest skojarzenie między delegata, a funkcja członkowska (program obsługi zdarzeń), która odpowiada wyzwolenie zdarzenia i umożliwia klientom z dowolnej klasy do zarejestrowania metod, które są zgodne z podpis i zwracany typ delegata bazowego.

Delegat może mieć co najmniej jeden skojarzone metody, które będzie wywoływany, gdy kod wskazuje, że wystąpiło zdarzenie. Zdarzenia w jednym programie mogą być udostępniane do innych programów, których platformą docelową .NET Framework środowisko uruchomieniowe języka wspólnego.

Istnieją dwa rodzaje zdarzeń deklaracje:

*elementy członkowskie danych zdarzeń*<br/>
Magazyn dla zdarzenia w formularzu elementu członkowskiego typu delegata jest tworzony przez kompilator dla zdarzenia element członkowski danych.  Element członkowski danych zdarzenia muszą być zadeklarowane wewnątrz klasy. To jest także znana jako zdarzenie proste (zobacz poniższy przykład kodu).

*bloki zdarzeń*<br/>
Bloki zdarzeń pozwalają dostosować zachowanie, Dodaj, Usuń i metod Zgłoś poprzez implementację, Dodaj, Usuń i zgłoś metod. Podpis metody Zgłoś Dodaj, Usuń i musi odpowiadać podpisowi delegata.  Blok zdarzeń nie są elementy członkowskie danych, a każde użycie jako element członkowski danych spowoduje wygenerowanie błędu kompilatora.

Zwracany typ procedury obsługi zdarzeń musi odpowiadać zwracany typ delegata.

W .NET Framework, można traktować element członkowski danych, tak jakby sama metoda (czyli `Invoke` metoda jego odpowiedniego delegata). Do deklarowania element członkowski danych zdarzenie zarządzane, należy wstępnie typ delegata. Z kolei metoda zdarzenie zarządzane niejawnie definiuje odpowiedniego zarządzanego obiektu delegowanego, jeśli nie jest już zdefiniowany.  Zobacz przykładowy kod na końcu tego tematu, na przykład.

Podczas deklarowania zdarzenie zarządzane, można określić dostępu, które będą wywoływane podczas obsługi zdarzeń są dodawane lub usuwane add i remove przy użyciu operatorów += i-=. Dodaj, Usuń i zgłoś metody może być wywoływana jawnie.

Poniższe kroki należy podjąć w celu tworzenia i używania zdarzenia w programie Visual C++:

1. Tworzenie lub identyfikowanie delegata. Jeśli zamierzasz zdefiniować własne zdarzenia, również upewnij się, że istnieje obiekt delegowany do za pomocą **zdarzeń** — słowo kluczowe. Jeśli wstępnie zdefiniowane zdarzenia w .NET Framework na przykład, następnie odbiorcy zdarzenia muszą jedynie znać nazwę delegata.

2. Utwórz klasę, która zawiera:

   - Zdarzenie utworzone na podstawie obiektu delegowanego.

   - (Opcjonalnie) Metoda, która sprawdza, czy wystąpienie delegata jest zadeklarowana za pomocą **zdarzeń** istnieje — słowo kluczowe. W przeciwnym razie ta logika muszą być umieszczone w kodzie, który wyzwala zdarzenie.

   - Metody, które wywołują zdarzenia. Te metody mogą być zastąpienia niektóre funkcje klasy bazowej.

   Ta klasa definiuje zdarzenia.

3. Należy zdefiniować co najmniej jedną klasę, łączących się zdarzenie z metod. Każda z tych klas zostanie skojarzony co najmniej jednej metody z zdarzenia w klasie bazowej.

4. Użyj zdarzenia:

   - Utwórz obiekt klasy, który zawiera deklarację zdarzeń.

   - Utwórz obiekt klasy, która zawiera definicji zdarzeń.

Aby uzyskać więcej informacji na temat języka C + +/ CLI zdarzenia, zobacz

- [Zdarzenia w interfejsie](../dotnet/how-to-use-events-in-cpp-cli.md)

### <a name="requirements"></a>Wymagania

— Opcja kompilatora: `/clr`

### <a name="examples"></a>Przykłady

Poniższy przykład kodu demonstruje deklarującego pary delegatów, zdarzenia i procedury obsługi zdarzeń; Subskrypcja (dodanie) procedury obsługi zdarzeń; wywoływanie programów obsługi zdarzeń; a następnie anulowania subskrypcji (usunięcie) procedury obsługi zdarzeń.

```cpp
// mcppv2_events.cpp
// compile with: /clr
using namespace System;

// declare delegates
delegate void ClickEventHandler(int, double);
delegate void DblClickEventHandler(String^);

// class that defines events
ref class EventSource {
public:
   event ClickEventHandler^ OnClick;   // declare the event OnClick
   event DblClickEventHandler^ OnDblClick;   // declare OnDblClick

   void FireEvents() {
      // raises events
      OnClick(7, 3.14159);
      OnDblClick("Hello");
   }
};

// class that defines methods that will called when event occurs
ref class EventReceiver {
public:
   void OnMyClick(int i, double d) {
      Console::WriteLine("OnClick: {0}, {1}", i, d);
   }

   void OnMyDblClick(String^ str) {
      Console::WriteLine("OnDblClick: {0}", str);
   }
};

int main() {
   EventSource ^ MyEventSource = gcnew EventSource();
   EventReceiver^ MyEventReceiver = gcnew EventReceiver();

   // hook handler to event
   MyEventSource->OnClick += gcnew ClickEventHandler(MyEventReceiver, &EventReceiver::OnMyClick);
   MyEventSource->OnDblClick += gcnew DblClickEventHandler(MyEventReceiver, &EventReceiver::OnMyDblClick);

   // invoke events
   MyEventSource->FireEvents();

   // unhook handler to event
   MyEventSource->OnClick -= gcnew ClickEventHandler(MyEventReceiver, &EventReceiver::OnMyClick);
   MyEventSource->OnDblClick -= gcnew DblClickEventHandler(MyEventReceiver, &EventReceiver::OnMyDblClick);
}
```

```Output
OnClick: 7, 3.14159

OnDblClick: Hello
```

Poniższy przykład kodu demonstruje przez logikę używaną do generowania `raise` metoda trivial zdarzeń: Jeśli zdarzenie ma co najmniej jeden subskrybentów, wywołanie `raise` metoda jawnie lub niejawnie wywołuje delegata. Jeśli delegat zwracany typ nie jest **void** i jeśli zero subskrybentów zdarzeń `raise` metoda zwraca wartość domyślna dla typu delegata. W przypadku subskrybentów zdarzeń podczas wywoływania `raise` metoda po prostu zwraca i jest zgłaszany żaden wyjątek. Jeśli delegat zwracany typ jest **void**, jest zwracany typ delegata.

```cpp
// trivial_events.cpp
// compile with: /clr /c
using namespace System;
public delegate int Del();
public ref struct C {
   int i;
   event Del^ MyEvent;

   void FireEvent() {
      i = MyEvent();
   }
};

ref struct EventReceiver {
   int OnMyClick() { return 0; }
};

int main() {
   C c;
   c.i = 687;

   c.FireEvent();
   Console::WriteLine(c.i);
   c.i = 688;

   EventReceiver^ MyEventReceiver = gcnew EventReceiver();
   c.MyEvent += gcnew Del(MyEventReceiver, &EventReceiver::OnMyClick);
   Console::WriteLine(c.i);
}
```

```Output
0

688
```

## <a name="see-also"></a>Zobacz też

[Component Extensions dla platform środowiska uruchomieniowego](../windows/component-extensions-for-runtime-platforms.md)