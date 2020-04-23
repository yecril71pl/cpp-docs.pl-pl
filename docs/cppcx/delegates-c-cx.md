---
title: Delegaty (C++/CX)
ms.date: 01/22/2017
ms.assetid: 3175bf1c-86d8-4eda-8d8f-c5b6753d8e38
ms.openlocfilehash: e570acafb8cce8b9496b79a062c3035015ba9811
ms.sourcegitcommit: 89d9e1cb08fa872483d1cde98bc2a7c870e505e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "82032476"
---
# <a name="delegates-ccx"></a>Delegaty (C++/CX)

Słowo `delegate` kluczowe służy do deklarowania typu odwołania, który jest odpowiednikiem środowiska wykonawczego systemu Windows obiektu funkcji w standardowym języku C++. Deklaracja delegata podobna do podpisu funkcji; określa typ zwracany i typy parametrów, które musi mieć jego funkcja opakowana. Jest to deklaracja delegata zdefiniowana przez użytkownika:

```cpp
public delegate void PrimeFoundHandler(int result);
```

Delegaci są najczęściej używane w połączeniu ze zdarzeniami. Zdarzenie ma typ delegata, w taki sam sposób, że klasa może mieć typ interfejsu. Pełnomocnik reprezentuje kontrakt, który programy obsługi zdarzeń wiele spełniają. Oto element członkowski klasy zdarzenia, którego typem jest wcześniej zdefiniowany pełnomocnik:

```cpp
event PrimeFoundHandler^ primeFoundEvent;
```

Podczas deklarowania delegatów, które będą udostępniane klientom w interfejsie binarnym aplikacji środowiska wykonawczego systemu Windows, należy użyć [systemu Windows::Foundation::TypedEventHandler\<TSender, TResult>](/uwp/api/windows.foundation.typedeventhandler-2). Ten pełnomocnik ma wstępnie zdefiniowane pliki binarne serwera proxy i skrótów, które umożliwiają korzystanie z niego przez klientów Javascript.

## <a name="consuming-delegates"></a>Korzystanie z delegatów

Podczas tworzenia aplikacji platformy systemu Windows, często pracować z pełnomocnikiem jako typ zdarzenia, które udostępnia klasy środowiska wykonawczego systemu Windows. Aby zasubskrybować zdarzenie, utwórz wystąpienie jego typu pełnomocnika, określając funkcję lub lambdę, która pasuje do podpisu delegata. Następnie użyj `+=` operatora, aby przekazać obiekt delegata do elementu członkowskiego zdarzenia w klasie. Jest to znane jako subskrybowanie zdarzenia. Gdy wystąpienie klasy "uruchamia" zdarzenie, funkcja jest wywoływana, wraz z innymi programami obsługi, które zostały dodane przez obiekt lub inne obiekty.

> [!TIP]
> Visual Studio wykonuje wiele pracy dla Ciebie podczas tworzenia programu obsługi zdarzeń. Na przykład jeśli określisz program obsługi zdarzeń w znacznikach XAML, pojawi się wskazówka narzędzia. Jeśli wybierzesz etykietkę narzędzia, program Visual Studio automatycznie utworzy metodę obsługi zdarzeń i skojarzy ją ze zdarzeniem w klasie publikowania.

W poniższym przykładzie przedstawiono podstawowy wzorzec. `Windows::Foundation::TypedEventHandler`jest typem delegata. Funkcja obsługi jest tworzona przy użyciu nazwanej funkcji.

W app.h:

[!code-cpp[cx_delegates#120](../cppcx/codesnippet/CPP/delegatesevents/class1.h#120)]

W app.cpp:

[!code-cpp[cx_delegates#121](../cppcx/codesnippet/CPP/delegatesevents/class1.cpp#121)]

> [!WARNING]
> Ogólnie rzecz biorąc dla programu obsługi zdarzeń lepiej jest użyć nazwanej funkcji zamiast lambda, chyba że należy bardzo uważać, aby uniknąć odwołań cyklicznych. Nazwana funkcja przechwytuje wskaźnik "this" przez słabe odwołanie, ale lambda przechwytuje go przez silne odwołanie i tworzy odwołanie cykliczne. Aby uzyskać więcej informacji, zobacz [Słabe odwołania i cykle przerywania](../cppcx/weak-references-and-breaking-cycles-c-cx.md).

Zgodnie z konwencją nazwy delegatów programu obsługi zdarzeń, które są zdefiniowane przez środowisko wykonawcze systemu Windows, mają formularz *EventHandler — na przykład RoutedEventHandler, SizeChangedEventHandler lub SuspendingEventHandler. Również zgodnie z konwencją delegatów obsługi zdarzeń mają dwa parametry i zwraca void. W pełnomocniku, który nie ma parametrów typu, pierwszym parametrem jest typ [Platform::Object^](../cppcx/platform-object-class.md); posiada odwołanie do nadawcy, który jest obiektem, który wywołał zdarzenie. Należy rzutować z powrotem do oryginalnego typu przed użyciem argumentu w metodzie obsługi zdarzeń. W pełnomocniku obsługi zdarzeń, który ma parametry typu, parametr pierwszego typu określa typ nadawcy, a drugi parametr jest dojściem do klasy ref, która przechowuje informacje o zdarzeniu. Zgodnie z konwencją \*tej klasy nosi nazwę EventArgs. Na przykład delegat RoutedEventHandler ma drugi parametr typu RoutedEventArgs^, a DragEventHander ma drugi parametr typu DragEventArgs^.

Zgodnie z konwencją delegatów, które zawijają kod, który jest wykonywany po zakończeniu operacji asynchroniiowej są nazywane *CompletedHandler. Te delegatów są zdefiniowane jako właściwości w klasie, a nie jako zdarzenia. W związku z tym nie `+=` używasz operatora, aby subskrybować je; wystarczy przypisać obiekt delegata do właściwości.

> [!TIP]
> Program IntelliSense języka C++ nie wyświetla pełnego podpisu delegata; w związku z tym nie pomaga określić określony typ EventArgs parametru. Aby znaleźć typ, można przejść do **przeglądarki** obiektów `Invoke` i spojrzeć na metodę pełnomocnika.

## <a name="creating-custom-delegates"></a>Tworzenie niestandardowych delegatów

Można zdefiniować własnych delegatów, zdefiniować programy obsługi zdarzeń lub umożliwić konsumentom przekazywanie w funkcji niestandardowych do składnika środowiska wykonawczego systemu Windows. Podobnie jak każdy inny typ środowiska wykonawczego systemu Windows, delegata publicznego nie można zadeklarować jako rodzajowy.

### <a name="declaration"></a>Deklaracji

Deklaracja delegata przypomina deklarację funkcji, z tą różnicą, że pełnomocnik jest typem. Zazwyczaj deklarujesz delegata w zakresie obszaru nazw, chociaż można również zagnieżdżać deklarację delegata w deklaracji klasy. Następujący delegat hermetyzuje dowolną funkcję, która `ContactInfo^` przyjmuje `Platform::String^`jako dane wejściowe i zwraca .

[!code-cpp[cx_delegates#111](../cppcx/codesnippet/CPP/delegatesevents/class1.h#111)]

Po zadeklarowaniu typu delegata, można zadeklarować członków klasy tego typu lub metody, które przyjmują obiekty tego typu jako parametry. Metoda lub funkcja może również zwrócić typ delegata. W poniższym przykładzie `ToCustomString` metoda przyjmuje delegata jako parametr wejściowy. Metoda umożliwia kod klienta, aby zapewnić funkcję niestandardową, która konstruuje ciąg `ContactInfo` z niektórych lub wszystkich właściwości publicznych obiektu.

[!code-cpp[Cx_delegates#112](../cppcx/codesnippet/CPP/delegatesevents/class1.h#112)]

> [!NOTE]
> Symbol "^" jest używany podczas odwoływania się do typu pełnomocnika, tak jak w przypadku dowolnego typu odwołania środowiska wykonawczego systemu Windows.

Deklaracja zdarzenia zawsze ma typ delegata. W tym przykładzie pokazano typowy podpis typu delegata w czasie wykonywania systemu Windows:

[!code-cpp[cx_delegates#122](../cppcx/codesnippet/CPP/delegatesevents/class1.h#122)]

Zdarzenie `Click` w `Windows:: UI::Xaml::Controls::Primitives::ButtonBase` klasie jest `RoutedEventHandler`typu . Aby uzyskać więcej informacji, zobacz [Zdarzenia](../cppcx/events-c-cx.md).

Kod klienta najpierw konstruuje `ref new` wystąpienie delegata przy użyciu i dostarczanie lambda, który jest zgodny z podpisem delegata i definiuje zachowanie niestandardowe.

[!code-cpp[Cx_delegates#113](../cppcx/codesnippet/CPP/delegatesevents/class1.cpp#113)]

Następnie wywołuje funkcję elementu członkowskiego i przekazuje pełnomocnika. `ci` Załóżmy, `ContactInfo^` że `textBlock` jest to `TextBlock^`wystąpienie i jest XAML .

[!code-cpp[Cx_delegates#114](../cppcx/codesnippet/CPP/delegatesevents/class1.cpp#114)]

W następnym przykładzie aplikacja kliencka przekazuje niestandardowego delegata do metody publicznej w składniku `Vector`środowiska wykonawczego systemu Windows, który wykonuje pełnomocnika względem każdego elementu w:

[!code-cpp[Cx_delegates#118](../cppcx/codesnippet/CPP/clientapp/mainpage.xaml.cpp#118)]

[!code-cpp[Cx_delegates#119](../cppcx/codesnippet/CPP/delegatesevents/class1.cpp#119)]

### <a name="construction"></a>Budownictwo

Można skonstruować pełnomocnika z dowolnego z tych obiektów:

- lambda

- funkcja statyczna

- wskaźnik do elementu członkowskiego

- std::funkcja

W poniższym przykładzie pokazano, jak skonstruować delegata z każdego z tych obiektów. Można użyć delegata w dokładnie taki sam sposób, niezależnie od typu obiektu, który jest używany do jego konstruowania.

[!code-cpp[Cx_delegates#115](../cppcx/codesnippet/CPP/delegatesevents/class1.cpp#115)]

> [!WARNING]
> Jeśli używasz lambda, który przechwytuje wskaźnik "this", należy `-=` użyć operatora jawnie odsłaniać ze zdarzenia przed zamknięciem lambda. Aby uzyskać więcej informacji, zobacz [Zdarzenia](../cppcx/events-c-cx.md).

### <a name="generic-delegates"></a>Delegaci ogólni

Delegatów ogólnego w języku C++/CX mają ograniczenia podobne do deklaracji klas rodzajowych. Nie można ich zadeklarować jako publicznych. Można zadeklarować prywatnego lub wewnętrznego delegata ogólnego i używać go z języka C++, ale klienci .NET lub JavaScript nie mogą go używać, ponieważ nie jest emitowany do metadanych .winmd. W tym przykładzie deklaruje ogólne delegata, który może być używane tylko przez C++:

[!code-cpp[Cx_delegates#116](../cppcx/codesnippet/CPP/delegatesevents/class1.h#116)]

W następnym przykładzie deklaruje wyspecjalizowane wystąpienie delegata wewnątrz definicji klasy:

[!code-cpp[Cx_delegates#117](../cppcx/codesnippet/CPP/delegatesevents/class1.h#117)]

## <a name="delegates-and-threads"></a>Pełnomocnicy i wątki

Delegat, podobnie jak obiekt funkcji, zawiera kod, który zostanie wykonany w pewnym momencie w przyszłości. Jeśli kod, który tworzy i przekazuje delegata i funkcja, która akceptuje i wykonuje delegata, są uruchomione w tym samym wątku, a następnie rzeczy są stosunkowo proste. Jeśli ten wątek jest wątku interfejsu użytkownika, a następnie delegata można bezpośrednio manipulować obiektów interfejsu użytkownika, takich jak formanty XAML.

Jeśli aplikacja kliencka ładuje składnik środowiska wykonawczego systemu Windows, który działa w mieszkaniu wątkowym i zapewnia delegata do tego składnika, a następnie domyślnie pełnomocnik jest wywoływany bezpośrednio w wątku STA. Większość składników środowiska wykonawczego systemu Windows można uruchomić w sta lub MTA.

Jeśli kod, który wykonuje pełnomocnika jest uruchomiony w innym wątku — na przykład w kontekście współbieżności::task object — użytkownik jest odpowiedzialny za synchronizację dostępu do udostępnionych danych. Na przykład jeśli delegat zawiera odwołanie do Vector, a formant XAML ma odwołanie do tego samego Vector, należy podjąć kroki, aby uniknąć zakleszczenia lub warunki wyścigu, które mogą wystąpić, gdy zarówno delegata i XAML kontroli próby uzyskania dostępu do Vector w tym samym czasie. Należy również zadbać, aby pełnomocnik nie próbuje przechwycić przez odwołanie zmiennych lokalnych, które mogą wyjść poza zakres, zanim pełnomocnik jest wywoływany.

Jeśli chcesz, aby utworzony delegat był wywoływany z powrotem w tym samym wątku, w który został utworzony — na przykład, jeśli przekażesz go do składnika uruchamianego w mieszkaniu `CallbackContext` MTA — i chcesz, aby był wywoływany w tym samym wątku co twórca, użyj przeciążenia konstruktora delegata, który przyjmuje drugi parametr. Użyj tego przeciążenia tylko dla delegatów, którzy mają zarejestrowany serwer proxy/skrót; nie wszystkie delegatów, które są zdefiniowane w windows.winmd są zarejestrowane.

Jeśli znasz programy obsługi zdarzeń w .NET, wiesz, że zalecaną praktyką jest, aby lokalna kopia zdarzenia przed jego pożarem. Pozwala to uniknąć warunków wyścigu, w którym program obsługi zdarzeń może zostać usunięty tuż przed wywołaniem zdarzenia. Nie jest to konieczne w języku C++/CX, ponieważ po dodaniu lub usunięciu nowej listy obsługi jest tworzona. Ponieważ obiekt C++ zwiększa liczbę odwołań na liście obsługi przed wywołaniem zdarzenia, jest gwarantowane, że wszystkie programy obsługi będą prawidłowe. Jednak oznacza to również, że jeśli usuniesz program obsługi zdarzeń w wątku zużywającym, ten program obsługi może nadal być wywoływany, jeśli obiekt publikowania nadal działa na jego kopii listy, która jest teraz nieaktualna. Obiekt publikowania nie otrzyma zaktualizowanej listy, dopóki następnym razem zostanie ono odpalone.

## <a name="see-also"></a>Zobacz też

[System typów](../cppcx/type-system-c-cx.md)<br/>
[Odwołanie do języka C++/CX](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[Dokumentacja przestrzeni nazw](../cppcx/namespaces-reference-c-cx.md)
