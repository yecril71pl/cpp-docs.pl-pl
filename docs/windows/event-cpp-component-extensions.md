---
title: zdarzenia (C++ Component Extensions) | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 7859b8b58bbd8765c38daea46efea5859ba61d67
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33881214"
---
# <a name="event--c-component-extensions"></a>event (C++ Component Extensions)
`event` Deklaruje — słowo kluczowe *zdarzeń*, czyli powiadomienia do subskrybentów w zarejestrowany (*procedury obsługi zdarzeń*) coś odsetek o wystąpieniu tego.  
  
## <a name="all-runtimes"></a>Wszystkie środowiska wykonawcze  
 C + +/ CX obsługuje deklarowanie *Członkowskiego zdarzenia* lub *bloku zdarzeń*. Element członkowski zdarzeń jest skrócona deklarowania bloku zdarzeń. Domyślnie deklaruje element członkowski zdarzeń `add()`, `remove()`, i `raise()` funkcje, które są zadeklarowane jawnie w bloku zdarzeń. Aby dostosować funkcje w elemencie członkowskim zdarzeń, zamiast tego zadeklarować bloku zdarzeń, a następnie zastąpić funkcje, które są potrzebne.  
  
 **Składnia**  
  
```  
  
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
  
 **Parametry**  
  
 *Modyfikator*  
 Modyfikator, które mogą być używane w deklaracji zdarzenia lub metoda dostępu zdarzenia.  Możliwe wartości to `static` i `virtual`.  
  
 *delegate*  
 [Delegować](../windows/delegate-cpp-component-extensions.md), którego sygnatura programu obsługi zdarzeń musi być zgodna.  
  
 *nazwa_zdarzenia*  
 Nazwa zdarzenia.  
  
 *RETURN_VALUE*  
 Wartość zwracaną metody dostępu zdarzeń.  Możliwe do zweryfikowania, zwracany typ musi być `void`.  
  
 *Parametry*  
 (opcjonalnie) Parametry `raise` metody, które odpowiadają podpisowi *delegować* parametru.  
  
 **Uwagi**  
  
 Zdarzenie jest skojarzenie delegata funkcji członkowskiej (procedura obsługi zdarzeń), która odpowiada wyzwolenie zdarzenia i umożliwia klientom z dowolnej klasy zarejestrować metody, które są zgodne z podpisem i zwracany typ delegata podstawowej.  
  
 Istnieją dwa rodzaje deklaracje zdarzeń:  
  
 *element członkowski danych zdarzeń*  
 Kompilator automatycznie tworzy magazynu dla zdarzenia w formularzu elementu członkowskiego typu delegata i tworzy wewnętrzny `add()`, `remove()`, i `raise()` funkcji elementów członkowskich. Element członkowski danych zdarzenia musi zostać zadeklarowany wewnątrz klasy. Zwracany typ zwracany typ delegata musi odpowiadać zwracanym typem obsługi zdarzeń.  
  
 *bloku zdarzeń*  
 Blok zdarzeń umożliwia jawnie deklarować i dostosować zachowanie `add()`, `remove()`, i `raise()` metody.  
  
 Można użyć `operators+=` i `operator-=` do dodawania i usuwania zdarzenia obsługi lub wywołanie `add()` i `remove()` metody jawnie.  
  
 `event` jest słowem kluczowym kontekstowa; zobacz [słowa kluczowe Context-Sensitive](../windows/context-sensitive-keywords-cpp-component-extensions.md) Aby uzyskać więcej informacji.  
  
## <a name="windows-runtime"></a>Środowisko wykonawcze systemu Windows  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [zdarzeń (C + +/ CX)](http://msdn.microsoft.com/library/windows/apps/hh755799.aspx).  
  
 Jeśli zamierzasz dodać, a następnie usuń program obsługi zdarzeń, musisz najpierw zapisać struktury EventRegistrationToken, która jest zwracana w wyniku operacji dodawania. Następnie w operacji usuwania, należy użyć zapisane struktury EventRegistrationToken do identyfikowania programu obsługi zdarzeń do usunięcia.  
  
### <a name="requirements"></a>Wymagania  
 — Opcja kompilatora: **/ZW**  
  
## <a name="common-language-runtime"></a>środowiska uruchomieniowe w trakcie wykonania 
 `event` — Słowo kluczowe pozwala zadeklarować zdarzenia. Zdarzenie jest sposób dla klasy zapewnienie powiadomienia, gdy coś zainteresowania sytuacji.  
  
 **Składnia**  
  
```  
  
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
  
 **Parametry**  
  
 *Modyfikator*  
 Modyfikator, które mogą być używane w deklaracji zdarzenia lub metoda dostępu zdarzenia.  Możliwe wartości to `static` i `virtual`.  
  
 *delegate*  
 [Delegować](../windows/delegate-cpp-component-extensions.md), którego sygnatura programu obsługi zdarzeń musi być zgodna.  
  
 *nazwa_zdarzenia*  
 Nazwa zdarzenia.  
  
 *RETURN_VALUE*  
 Wartość zwracaną metody dostępu zdarzeń.  Możliwe do zweryfikowania, zwracany typ musi być `void`.  
  
 *Parametry*  
 (opcjonalnie) Parametry `raise` metody, które odpowiadają podpisowi *delegować* parametru.  
  
 **Uwagi**  
  
 Zdarzenie jest skojarzenie delegata funkcji członkowskiej (procedura obsługi zdarzeń), która odpowiada wyzwolenie zdarzenia i umożliwia klientom z dowolnej klasy zarejestrować metody, które są zgodne z podpisem i zwracany typ delegata podstawowej.  
  
 Delegat może mieć co najmniej jedną metodę skojarzony, które będą wywoływane po kodzie wskazuje, że wystąpiło zdarzenie. Zdarzenia w jednym programie można udostępnione innych programów o docelowej wersji .NET Framework środowisko uruchomieniowe języka wspólnego.  
  
 Istnieją dwa rodzaje deklaracje zdarzeń:  
  
 *elementy członkowskie danych zdarzeń*  
 Magazyn dla zdarzenia w formularzu elementu członkowskiego typu delegata, jest tworzony przez kompilator dla elementu członkowskiego danych dotyczących zdarzeń.  Element członkowski danych zdarzenia musi zostać zadeklarowany wewnątrz klasy. To jest także znana jako trivial zdarzenia (zobacz poniższy przykład kodu).  
  
 *bloki zdarzeń*  
 Bloki zdarzeń pozwalają dostosować zachowanie Dodaj, Usuń i metod Zgłoś, implementując Dodaj, Usuń i zgłoś metody. Podpis metody Zgłoś Dodaj, Usuń i musi być zgodna podpis delegata.  Zdarzenie bloku zdarzenia nie są elementy członkowskie danych, a każde użycie jako element członkowski danych zostanie wygenerowany błąd kompilatora. 
  
 Zwracany typ obsługi zdarzeń musi odpowiadać zwracanym typem obiektu delegowanego.  
  
 W programie .NET Framework można traktować elementu członkowskiego danych tak, jakby była samej metody (oznacza to, `Invoke` metody swojego delegata odpowiedniego). Typ delegata musi wstępnie deklarowania element danych zarządzanych zdarzeń. Z kolei metody zarządzanych zdarzeń niejawnie definiuje odpowiedniego delegata zarządzanych, jeśli nie jest już zdefiniowany.  Zobacz przykładowy kod na końcu tego tematu, na przykład.  
  
 Przy deklarowaniu zarządzanych zdarzeń, można określić Dodawanie i usuwanie metody dostępu, które będą wywoływane podczas dodawania lub usuwania programów obsługi zdarzeń przy użyciu operatorów += i-=. Można jawnie wywołać metody dodawania, usuwania i zgłoś.  
  
 Poniższe kroki należy podjąć w celu tworzenia i używania zdarzeń w programie Visual C++:  
  
1.  Tworzenie lub identyfikowanie delegata. Jeśli definiujesz własne zdarzenia, upewnij się czy jest delegata do użycia z `event` — słowo kluczowe. Jeśli wstępnie zdefiniowane zdarzenie w programie .NET Framework na przykład, następnie konsumentów zdarzenia muszą tylko znać nazwę delegata.  
  
2.  Utwórz klasę, która zawiera:  
  
    -   Zdarzenie utworzone na podstawie obiektu delegowanego.  
  
    -   (opcjonalnie) Metoda, która sprawdza, czy wystąpienia delegata zadeklarowana z `event` istnieje — słowo kluczowe. W przeciwnym razie ta logiki muszą znajdować się w kodzie, który wyzwala zdarzenie.  
  
    -   Metody, które wywołują zdarzenia. Te metody mogą być zastąpienia niektóre funkcje klasy podstawowej.  
  
     Ta klasa definiuje zdarzenia.  
  
3.  Zdefiniuj co najmniej jedną klasę łączących się zdarzenie z metod. Każda z tych klas zostanie skojarzony co najmniej jednej metody z zdarzenia w klasie podstawowej.  
  
4.  Użyj zdarzenia:  
  
    -   Utwórz obiekt klasy, która zawiera deklaracji zdarzenia.  
  
    -   Utwórz obiekt klasy, która zawiera definicji zdarzeń.  
  
 Aby uzyskać więcej informacji na temat języka C + +/ CLI zdarzenia, zobacz  
  
-   [Zdarzenia w interfejsie](../dotnet/how-to-use-events-in-cpp-cli.md)  
  
### <a name="requirements"></a>Wymagania  
 — Opcja kompilatora:   **/CLR**  
  
### <a name="examples"></a>Przykłady  
 **Przykład**  
  
 Poniższy przykład kodu pokazuje deklarujący pary delegatów, zdarzeń i procedury obsługi zdarzeń; Subskrypcja (Dodawanie) programów obsługi zdarzeń; wywoływanie programów obsługi zdarzeń; a następnie anulowanie (usuwanie) obsługi zdarzeń.  
  
```  
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
  
 **Output**  
  
```Output  
OnClick: 7, 3.14159  
  
OnDblClick: Hello  
```  
  
 **Przykład**  
  
 Poniższy przykład kodu pokazuje przez logikę używaną do generowania `raise` metody zdarzenia prosta: Jeśli zdarzenie ma co najmniej jeden subskrybentów, wywoływania `raise` metoda jawnie lub niejawnie wywołuje delegata. Jeśli delegat zwracany typ nie jest `void` i nie będą zero subskrybentów zdarzeń `raise` metoda zwraca wartość domyślna dla typu delegata. Jeśli nie ma żadnych subskrybentów zdarzeń, wywoływania `raise` metoda po prostu zwraca i nie jest zgłaszany wyjątek nie. Jeśli delegat zwracany typ jest `void`, jest zwracany typ delegata.  
  
```  
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
  
 **Output**  
  
```Output  
0  
  
688  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Component Extensions dla platform środowiska uruchomieniowego](../windows/component-extensions-for-runtime-platforms.md)