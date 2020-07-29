---
title: Delegaty (C++/CX)
ms.date: 01/22/2017
ms.assetid: 3175bf1c-86d8-4eda-8d8f-c5b6753d8e38
ms.openlocfilehash: 4944efc10b4590f8dc682230968d9c97ef91cb5c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225777"
---
# <a name="delegates-ccx"></a>Delegaty (C++/CX)

**`delegate`** Słowo kluczowe jest używane do deklarowania typu referencyjnego, który jest odpowiednikiem środowisko wykonawcze systemu Windows obiektu funkcji w standardowym języku C++. Deklaracja delegata podobna do sygnatury funkcji; Określa typ zwracany i typy parametrów, które musi zawierać funkcja opakowana. Jest to zdefiniowana przez użytkownika deklaracja delegata:

```cpp
public delegate void PrimeFoundHandler(int result);
```

Delegaty są najczęściej używane w połączeniu z zdarzeniami. Zdarzenie ma typ delegata, tak samo, jak Klasa może mieć typ interfejsu. Delegat reprezentuje kontrakt, który jest bardzo spełniający procedury obsługi zdarzeń. Oto element członkowski klasy zdarzeń, którego typem jest zdefiniowany wcześniej delegat:

```cpp
event PrimeFoundHandler^ primeFoundEvent;
```

Podczas deklarowania delegatów, którzy będą narażeni na klientów za pośrednictwem interfejsu binarnego aplikacji środowisko wykonawcze systemu Windows, użyj [systemu Windows: \<TSender, TResult> : Foundation:: TypedEventHandler](/uwp/api/windows.foundation.typedeventhandler-2). Ten delegat ma wstępnie zdefiniowane pliki binarne proxy i zastępcze, które umożliwiają korzystanie z nich przez klientów JavaScript.

## <a name="consuming-delegates"></a>Zużywanie delegatów

Podczas tworzenia aplikacji platforma uniwersalna systemu Windows często pracujesz z delegatem jako typem zdarzenia, które uwidacznia Klasa środowisko wykonawcze systemu Windows. Aby subskrybować zdarzenie, Utwórz wystąpienie jego typu delegata, określając funkcję — lub wyrażenie lambda, które pasuje do sygnatury delegata. Następnie użyj `+=` operatora, aby przekazać obiekt delegata do elementu członkowskiego zdarzenia w klasie. Jest to tzw. subskrybowanie zdarzenia. Gdy wystąpienie klasy "wyzwala" zdarzenie, wywoływana jest funkcja wraz z innymi dodziałami, które zostały dodane przez obiekt lub inne obiekty.

> [!TIP]
> Program Visual Studio wykonuje dużą nakład pracy podczas tworzenia programu obsługi zdarzeń. Na przykład jeśli określisz procedurę obsługi zdarzeń w znaczniku XAML, zostanie wyświetlona etykietka narzędzia. W przypadku wybrania etykietki narzędzia program Visual Studio automatycznie tworzy metodę obsługi zdarzeń i kojarzy ją ze zdarzeniem klasy Publishing.

Poniższy przykład pokazuje wzorzec podstawowy. `Windows::Foundation::TypedEventHandler`jest typem delegata. Funkcja obsługi jest tworzona za pomocą nazwanej funkcji.

W aplikacji App. h:

[!code-cpp[cx_delegates#120](../cppcx/codesnippet/CPP/delegatesevents/class1.h#120)]

W aplikacji App. cpp:

[!code-cpp[cx_delegates#121](../cppcx/codesnippet/CPP/delegatesevents/class1.cpp#121)]

> [!WARNING]
> Ogólnie rzecz biorąc, w przypadku programu obsługi zdarzeń lepiej jest używać nazwanej funkcji zamiast wyrażenia lambda, chyba że chcesz uniknąć cyklicznych odwołań. Nazwana funkcja przechwytuje wskaźnik "This" przez słabe odwołanie, ale lambda przechwytuje je przez silną referencję i tworzy odwołanie cykliczne. Aby uzyskać więcej informacji, zobacz [słabe odwołania i cykle przerywania](../cppcx/weak-references-and-breaking-cycles-c-cx.md).

Według Konwencji nazwy delegatów obsługi zdarzeń zdefiniowane przez środowisko wykonawcze systemu Windows mają postać * EventHandler — na przykład RoutedEventHandler, SizeChangedEventHandler lub SuspendingEventHandler. Ponadto według Konwencji delegatów obsługi zdarzeń ma dwa parametry i zwracają typ void. W delegatze, który nie ma parametrów typu, pierwszy parametr jest typu [platform:: Object ^](../cppcx/platform-object-class.md); Przechowuje odwołanie do nadawcy, który jest obiektem, który wygenerował zdarzenie. Przed użyciem argumentu w metodzie obsługi zdarzeń należy wykonać rzutowanie na oryginalny typ. W delegatze obsługi zdarzeń, który ma parametry typu, pierwszy parametr typu określa typ nadawcy, a drugi parametr jest dojściem do klasy referencyjnej, która zawiera informacje o zdarzeniu. Według Konwencji Ta klasa ma nazwę \* EventArgs. Na przykład delegat RoutedEventHandler ma drugi parametr typu RoutedEventArgs ^, a DragEventHander ma drugi parametr typu DragEventArgs ^.

Zgodnie z Konwencją Delegaty zawijają kod, który jest wykonywany po zakończeniu operacji asynchronicznej o nazwie * CompletedHandler. Te Delegaty są zdefiniowane jako właściwości w klasie, a nie jako zdarzenia. W związku z tym nie należy używać `+=` operatora, aby subskrybować te elementy; wystarczy przypisać obiekt delegata do właściwości.

> [!TIP]
> Funkcja IntelliSense języka C++ nie pokazuje pełnego podpisu delegata; w związku z tym nie pomaga określić określonego typu parametru EventArgs. Aby znaleźć typ, możesz przejść do **Przeglądarka obiektów** i przyjrzeć się `Invoke` metodzie delegata.

## <a name="creating-custom-delegates"></a>Tworzenie niestandardowych delegatów

Możesz zdefiniować własnych delegatów, aby zdefiniować programy obsługi zdarzeń lub umożliwić użytkownikom przekazywanie funkcji niestandardowych do składnika środowisko wykonawcze systemu Windows. Podobnie jak w przypadku dowolnego innego typu środowisko wykonawcze systemu Windows delegat publiczny nie może być zadeklarowany jako generyczny.

### <a name="declaration"></a>Oświadczeń

Deklaracja delegata jest podobna do deklaracji funkcji, z tą różnicą, że delegat jest typem. Zwykle deklaruje delegata w zakresie przestrzeni nazw, chociaż można także zagnieżdżać deklarację delegata w deklaracji klasy. Następujący delegat hermetyzuje każdą funkcję, która przyjmuje `ContactInfo^` jako dane wejściowe i zwraca `Platform::String^` .

[!code-cpp[cx_delegates#111](../cppcx/codesnippet/CPP/delegatesevents/class1.h#111)]

Po zadeklarowaniu typu delegata można zadeklarować składowe klasy tego typu lub metod, które pobierają obiekty tego typu jako parametry. Metoda lub funkcja może również zwracać typ delegata. W poniższym przykładzie `ToCustomString` Metoda przyjmuje delegat jako parametr wejściowy. Metoda umożliwia kodowi klienta dostarczanie funkcji niestandardowej, która konstruuje ciąg z niektórych lub wszystkich właściwości publicznych `ContactInfo` obiektu.

[!code-cpp[Cx_delegates#112](../cppcx/codesnippet/CPP/delegatesevents/class1.h#112)]

> [!NOTE]
> Symbol "^" jest używany podczas odwoływania się do typu delegata, podobnie jak w przypadku dowolnego środowisko wykonawcze systemu Windows typu odwołania.

Deklaracja zdarzenia zawsze ma typ delegata. Ten przykład przedstawia typowy podpis typu delegata w środowisko wykonawcze systemu Windows:

[!code-cpp[cx_delegates#122](../cppcx/codesnippet/CPP/delegatesevents/class1.h#122)]

`Click`Zdarzenie w `Windows:: UI::Xaml::Controls::Primitives::ButtonBase` klasie jest typu `RoutedEventHandler` . Aby uzyskać więcej informacji, zobacz [zdarzenia](../cppcx/events-c-cx.md).

Kod klienta najpierw Konstruuje wystąpienie delegata przy użyciu `ref new` i dostarczając wyrażenie lambda, które jest zgodne z sygnaturą delegata i definiuje zachowanie niestandardowe.

[!code-cpp[Cx_delegates#113](../cppcx/codesnippet/CPP/delegatesevents/class1.cpp#113)]

Następnie wywołuje funkcję członkowską i przekazuje delegata. Załóżmy, że `ci` jest `ContactInfo^` wystąpieniem i `textBlock` jest XAML `TextBlock^` .

[!code-cpp[Cx_delegates#114](../cppcx/codesnippet/CPP/delegatesevents/class1.cpp#114)]

W następnym przykładzie aplikacja kliencka przekazuje niestandardowego delegata do metody publicznej w składniku środowisko wykonawcze systemu Windows, który wykonuje delegata dla każdego elementu w `Vector` :

[!code-cpp[Cx_delegates#118](../cppcx/codesnippet/CPP/clientapp/mainpage.xaml.cpp#118)]

[!code-cpp[Cx_delegates#119](../cppcx/codesnippet/CPP/delegatesevents/class1.cpp#119)]

### <a name="construction"></a>Budownictwo

Delegat można skonstruować z dowolnego z następujących obiektów:

- lambda

- funkcja statyczna

- wskaźnik do elementu członkowskiego

- std:: Function

Poniższy przykład pokazuje, jak utworzyć delegata z każdego z tych obiektów. Delegat jest używany w taki sam sposób, niezależnie od typu obiektu, który służy do konstruowania go.

[!code-cpp[Cx_delegates#115](../cppcx/codesnippet/CPP/delegatesevents/class1.cpp#115)]

> [!WARNING]
> Jeśli używasz wyrażenia lambda, które przechwytuje wskaźnik "This", pamiętaj, aby użyć `-=` operatora, aby jawnie wyrejestrować ze zdarzenia przed wyjściem z wyrażenia lambda. Aby uzyskać więcej informacji, zobacz [zdarzenia](../cppcx/events-c-cx.md).

### <a name="generic-delegates"></a>Delegaci ogólni

Delegaty generyczne w języku C++/CX mają ograniczenia podobne do deklaracji klas ogólnych. Nie mogą być deklarowane jako publiczne. Można zadeklarować prywatny lub wewnętrzny Delegat ogólny i korzystać z niego z języka C++, ale klienci .NET lub JavaScript nie mogą go wykorzystać, ponieważ nie są emitowane do metadanych. winmd. Ten przykład deklaruje delegata generycznego, który może być użyty tylko przez C++:

[!code-cpp[Cx_delegates#116](../cppcx/codesnippet/CPP/delegatesevents/class1.h#116)]

Następny przykład deklaruje wyspecjalizowane wystąpienie delegata wewnątrz definicji klasy:

[!code-cpp[Cx_delegates#117](../cppcx/codesnippet/CPP/delegatesevents/class1.h#117)]

## <a name="delegates-and-threads"></a>Obiekty delegowane i wątki

Delegat, podobnie jak obiekt Function, zawiera kod, który będzie wykonywany w pewnym czasie w przyszłości. Jeśli kod, który tworzy i przekazuje delegata, a funkcja, która akceptuje i wykonuje delegata, działa w tym samym wątku, wówczas elementy są stosunkowo proste. Jeśli ten wątek jest wątkiem interfejsu użytkownika, delegat może bezpośrednio manipulować obiektami interfejsu użytkownika, takimi jak kontrolki XAML.

Jeśli aplikacja kliencka załaduje składnik środowisko wykonawcze systemu Windows, który działa w Apartament wątkowy i udostępnia delegatowi ten składnik, domyślnie delegat jest wywoływany bezpośrednio w wątku STA. Większość składników środowisko wykonawcze systemu Windows można uruchamiać w WĄTKach lub MTA.

Jeśli kod, który wykonuje delegata jest uruchomiony w innym wątku — na przykład w kontekście obiektu concurrency:: Task — użytkownik jest odpowiedzialny za synchronizację dostępu do udostępnionych danych. Na przykład, jeśli delegat zawiera odwołanie do wektora, a kontrolka XAML odwołuje się do tego samego wektora, należy wykonać kroki w celu uniknięcia zakleszczenia lub sytuacji wyścigu, które mogą wystąpić, gdy zarówno obiekt delegowany, jak i formant XAML próbuje uzyskać dostęp do wektora w tym samym czasie. Należy również zadbać o to, aby delegat nie podejmował prób przechwycenia przez odniesienia lokalne zmienne, które mogą wykraczać poza zakres przed wywołaniem delegata.

Jeśli chcesz, aby utworzony delegat został wywołany w tym samym wątku, w którym został utworzony — na przykład, Jeśli przekażesz go do składnika, który działa w komórce MTA, i chcesz go wywołać w tym samym wątku co twórca, Użyj przeciążenia konstruktora delegata, który przyjmuje drugi `CallbackContext` parametr. Tego przeciążenia należy używać tylko w delegatach, które mają zarejestrowany serwer proxy/zastępczy; nie wszystkie Delegaty zdefiniowane w systemie Windows. winmd są zarejestrowane.

Jeśli znasz programy obsługi zdarzeń w programie .NET, wiesz, że zalecaną metodą jest wykonanie lokalnej kopii zdarzenia przed jego wyzwoleniem. Pozwala to uniknąć sytuacji wyścigu, w których program obsługi zdarzeń może zostać usunięty tuż przed wywołaniem zdarzenia. Nie jest to konieczne w języku C++/CX, ponieważ w przypadku dodania lub usunięcia obsługi zdarzeń zostanie utworzona nowa lista obsługi. Ponieważ obiekt C++ zwiększa liczbę odwołań na liście programu obsługi przed wywołaniem zdarzenia, gwarantuje to, że wszystkie programy obsługi będą prawidłowe. Oznacza to jednak, że w przypadku usunięcia programu obsługi zdarzeń w wątku zużywania, ten program obsługi może być nadal wywoływany, jeśli obiekt publikacji nadal działa na jego kopii listy, która jest teraz nieaktualna. Obiekt publikacji nie uzyska zaktualizowanej listy do momentu następnego uruchomienia zdarzenia.

## <a name="see-also"></a>Zobacz także

[System typów](../cppcx/type-system-c-cx.md)<br/>
[Dokumentacja języka C++/CX](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[Dokumentacja przestrzeni nazw](../cppcx/namespaces-reference-c-cx.md)
