---
title: zdarzenie (C++/CLI i C++/CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- event
- event_cpp
helpviewer_keywords:
- event keyword [C++]
ms.assetid: c4998e42-883c-4419-bbf4-36cdc979dd27
ms.openlocfilehash: 90682ba699f6316cb6b38a3b78c44e853cd5473f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80172389"
---
# <a name="event--ccli-and-ccx"></a>zdarzenie (C++/CLI i C++/CX)

Słowo kluczowe **zdarzenia** deklaruje *zdarzenie*, które jest powiadomieniem do zarejestrowanych subskrybentów (*programy obsługi zdarzeń*), które miały coś interesu.

## <a name="all-runtimes"></a>Wszystkie środowiska wykonawcze

C++/CX obsługuje deklarowanie *elementu członkowskiego zdarzenia* lub *bloku zdarzeń*. Element członkowski zdarzenia jest skrótem do deklarowania bloku zdarzeń. Domyślnie członek zdarzenia deklaruje funkcje `add()`, `remove()`i `raise()`, które są zadeklarowane jawnie w bloku zdarzeń. Aby dostosować funkcje w składowej zdarzenia, zadeklaruj blok zdarzenia zamiast tego, a następnie zastąp wymagane funkcje.

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

*modyfikator*<br/>
Modyfikator, który może być używany w deklaracji zdarzenia lub metodzie dostępu do zdarzeń.  Możliwe wartości są **statyczne** i **wirtualne**.

*delegate*<br/>
[Delegat](delegate-cpp-component-extensions.md), którego sygnatura musi być zgodna z programem obsługi zdarzeń.

*event_name*<br/>
Nazwa zdarzenia.

*return_value*<br/>
Wartość zwracana metody dostępu do zdarzenia.  Aby można było zweryfikować, zwracany typ musi być typem **void**.

*parameters*<br/>
obowiązkowe Parametry metody `raise`, które pasują do sygnatury parametru *delegata* .

### <a name="remarks"></a>Uwagi

Zdarzenie jest skojarzeniem między delegatem a funkcją członkowską (procedura obsługi zdarzeń), która reaguje na Wyzwalanie zdarzenia i umożliwia klientom z dowolnej klasy rejestrowanie metod, które są zgodne z sygnaturą i zwracanym typem źródłowego delegata.

Istnieją dwa rodzaje deklaracji zdarzeń:

*element członkowski danych zdarzenia*<br/>
Kompilator automatycznie tworzy magazyn dla zdarzenia w postaci elementu członkowskiego typu delegata, a następnie tworzy wewnętrzne `add()`, `remove()`i `raise()` funkcje składowe. Składowa danych zdarzenia musi być zadeklarowana wewnątrz klasy. Zwracany typ typu zwracanego delegata musi być zgodny z typem zwracanym programu obsługi zdarzeń.

*blok zdarzeń*<br/>
Blok zdarzeń umożliwia jawne deklarowanie i Dostosowywanie zachowania `add()`, `remove()`i `raise()` metod.

**Operatory + =** i **operator-=** umożliwiają dodawanie i usuwanie programu obsługi zdarzeń lub wywołaj metody `add()` i `remove()` jawnie.

**zdarzenie** jest kontekstowego słowa kluczowego; Aby uzyskać więcej informacji, zobacz [kontekstowe słowa kluczowe](context-sensitive-keywords-cpp-component-extensions.md) .

## <a name="windows-runtime"></a>Środowisko wykonawcze systemu Windows

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [EventsC++(/CX)](../cppcx/events-c-cx.md).

Jeśli zamierzasz dodać, a następnie usunąć procedurę obsługi zdarzeń, musisz zapisać strukturę EventRegistrationToken, która jest zwracana przez operację dodawania. Następnie w operacji usuwania należy użyć zapisanej struktury EventRegistrationToken, aby zidentyfikować procedurę obsługi zdarzeń, która ma zostać usunięta.

### <a name="requirements"></a>Wymagania

Opcja kompilatora: `/ZW`

## <a name="common-language-runtime"></a>środowiska uruchomieniowe w trakcie wykonania

Słowo kluczowe **zdarzenia** umożliwia zadeklarowanie zdarzenia. Zdarzenie to sposób, w jaki Klasa dostarcza powiadomienia, gdy wystąpi coś zainteresowania.

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

*modyfikator*<br/>
Modyfikator, który może być używany w deklaracji zdarzenia lub metodzie dostępu do zdarzeń.  Możliwe wartości są **statyczne** i **wirtualne**.

*delegate*<br/>
[Delegat](delegate-cpp-component-extensions.md), którego sygnatura musi być zgodna z programem obsługi zdarzeń.

*event_name*<br/>
Nazwa zdarzenia.

*return_value*<br/>
Wartość zwracana metody dostępu do zdarzenia.  Aby można było zweryfikować, zwracany typ musi być typem **void**.

*parameters*<br/>
obowiązkowe Parametry metody `raise`, które pasują do sygnatury parametru *delegata* .

### <a name="remarks"></a>Uwagi

Zdarzenie jest skojarzeniem między delegatem a funkcją członkowską (procedura obsługi zdarzeń), która reaguje na Wyzwalanie zdarzenia i umożliwia klientom z dowolnej klasy rejestrowanie metod, które są zgodne z sygnaturą i zwracanym typem źródłowego delegata.

Delegat może mieć jedną lub więcej skojarzonych metod, które będą wywoływane, gdy kod wskazuje, że zdarzenie wystąpiło. Zdarzenie w jednym programie można udostępnić innym programom przeznaczonym dla .NET Framework środowiska uruchomieniowego języka wspólnego.

Istnieją dwa rodzaje deklaracji zdarzeń:

*elementy członkowskie danych zdarzenia*<br/>
Magazyn dla zdarzenia w formie elementu członkowskiego typu delegata jest tworzony przez kompilator dla zdarzeń elementu członkowskiego danych.  Składowa danych zdarzenia musi być zadeklarowana wewnątrz klasy. Jest to również znane jako zdarzenie proste (Zobacz przykład kodu poniżej).

*bloki zdarzeń*<br/>
Bloki zdarzeń pozwalają dostosować zachowanie metod dodawania, usuwania i wywoływania, implementując metody dodawania, usuwania i wywoływania. Sygnatura metod dodawania, usuwania i wywoływania musi być zgodna z podpisem delegata.  Zdarzenia bloku zdarzeń nie są elementami członkowskimi danych, a żadne użycie jako element członkowski danych spowoduje wygenerowanie błędu kompilatora.

Zwracany typ procedury obsługi zdarzeń musi być zgodny z typem zwracanym delegata.

W .NET Framework można traktować składową danych tak, jakby była to sama metoda (czyli `Invoke` Metoda odpowiadającego mu delegata). Należy wstępnie zdefiniować typ delegata do deklarowania elementu członkowskiego danych zdarzenia zarządzanego. W przeciwieństwie do zarządzanej metody zdarzenia niejawnie definiuje odpowiadającą zarządzaną delegata, jeśli nie jest jeszcze zdefiniowana.  Przykład zawiera przykładowy kod na końcu tego tematu.

Podczas deklarowania zdarzenia zarządzanego można określić metody dostępu Add i Remove, które będą wywoływane, gdy programy obsługi zdarzeń zostaną dodane lub usunięte przy użyciu operatorów + = i-=. Metody dodawania, usuwania i wywoływania mogą być wywoływane jawnie.

Aby można było tworzyć i używać zdarzeń w wizualizacji C++, należy wykonać następujące czynności:

1. Utwórz lub Zidentyfikuj delegata. W przypadku definiowania własnego zdarzenia należy również upewnić się, że istnieje delegat do użycia ze słowem kluczowym **zdarzenia** . Jeśli zdarzenie jest wstępnie zdefiniowane, w .NET Framework na przykład, odbiorcy zdarzenia muszą znać nazwę delegata.

2. Utwórz klasę zawierającą:

   - Zdarzenie utworzone na podstawie delegata.

   - Obowiązkowe Metoda, która sprawdza, czy wystąpienie delegata zadeklarowane za pomocą słowa kluczowego **zdarzenia** istnieje. W przeciwnym razie logika musi być umieszczona w kodzie, który uruchamia zdarzenie.

   - Metody wywołujące zdarzenie. Metody te można zastępować w niektórych funkcjach klasy podstawowej.

   Ta klasa definiuje zdarzenie.

3. Zdefiniuj co najmniej jedną klasę, która łączy metody ze zdarzeniem. Każda z tych klas spowoduje skojarzenie jednej lub więcej metod ze zdarzeniem w klasie bazowej.

4. Użyj zdarzenia:

   - Utwórz obiekt klasy, która zawiera deklarację zdarzenia.

   - Utwórz obiekt klasy, która zawiera definicję zdarzenia.

Aby uzyskać więcej informacji C++o zdarzeniach/CLI, zobacz

- [Zdarzenia w interfejsie](../dotnet/how-to-use-events-in-cpp-cli.md)

### <a name="requirements"></a>Wymagania

Opcja kompilatora: `/clr`

### <a name="examples"></a>Przykłady

Poniższy przykład kodu ilustruje deklarowanie par delegatów, zdarzeń i obsługi zdarzeń; Subskrybowanie (Dodawanie) obsługi zdarzeń; Wywoływanie programów obsługi zdarzeń; a następnie Anuluj subskrypcję (usuwając) programów obsługi zdarzeń.

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

Poniższy przykład kodu demonstruje logikę używaną do generowania metody `raise` prostego zdarzenia: Jeśli zdarzenie ma jednego lub więcej subskrybentów, wywołanie metody `raise` niejawnie lub jawnie wywołuje delegata. Jeśli typ zwracany delegata nie jest typem **void** i jeśli nie istnieją Subskrybenci zdarzeń, Metoda `raise` zwraca wartość domyślną dla typu delegata. Jeśli nie ma subskrybentów zdarzeń, wywołanie metody `raise` po prostu zwróci i nie zostanie zgłoszony żaden wyjątek. Jeśli typ zwracany delegata nie jest typem **void**, zwracany jest typ delegata.

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

[Rozszerzenia składników dla platformy .NET i platformy uniwersalnej systemu Windows](component-extensions-for-runtime-platforms.md)
