---
title: Delegates (C++/CX)
ms.date: 01/22/2017
ms.assetid: 3175bf1c-86d8-4eda-8d8f-c5b6753d8e38
ms.openlocfilehash: e2158adad288045c9a98889dbe97e834dc93ea71
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62406928"
---
# <a name="delegates-ccx"></a>Delegates (C++/CX)

`delegate` — Słowo kluczowe jest używane do deklarowania typu odwołania, który jest odpowiednikiem obiektu funkcyjnego w standardzie języka C++ środowiska wykonawczego Windows. Deklaracja delegata, podobny do podpisu funkcji. Określa typ zwracany i typy parametrów, które jej opakowana funkcja musi mieć. Jest to deklaracja delegata użytkownika:

```cpp
public delegate void PrimeFoundHandler(int result);
```

Delegaty są najczęściej używane w połączeniu ze zdarzeniami. Zdarzenie ma typ delegata w taki, taki sam sposób, że klasa może mieć typu interfejsu. Reprezentuje obiekt delegowany kontraktu, który znacznie wykonać procedury obsługi zdarzeń. Oto składowej klasy zdarzeń, którego typ jest delegatem uprzednio zdefiniowany:

```cpp
event PrimeFoundHandler^ primeFoundEvent;
```

Podczas deklarowania obiektów delegowanych, które będą dostępne dla klientów między interfejsem binarnym aplikacji środowiska wykonawczego Windows, użyj [Windows::Foundation:: typedeventhandler\<TSender, TResult >](/uwp/api/windows.foundation.typedeventhandler). Ten delegat jest wstępnie zdefiniowane serwera proxy i klas zastępczych pliki binarne, które umożliwiają go do użycia przez klientów języka Javascript.

## <a name="consuming-delegates"></a>Korzystanie z obiektów delegowanych

Podczas tworzenia aplikacji uniwersalnych platformy Windows często pracują z delegatem, jako typ zdarzenia, które udostępnia klasy środowiska wykonawczego Windows. Aby subskrybować zdarzenie, Utwórz wystąpienie obiektu jego typ delegowany, określając funkcji — lub lambda, które odpowiadają podpisowi delegata. Następnie użyj `+=` operatora do przekazania obiektu delegowanego do elementu członkowskiego zdarzenia w klasie. Jest to nazywane subskrybowanie zdarzenia. Jeśli wystąpienie klasy"" zdarzenia, Twoja funkcja jest wywoływana wraz z innych programów obsługi, które zostały dodane przez obiekt lub innych obiektów.

> [!TIP]
> Program Visual Studio sporego nakładu pracy dla Ciebie podczas tworzenia programu obsługi zdarzeń. Na przykład jeśli określisz program obsługi zdarzeń w znaczniku XAML, pojawi się etykietka narzędzia. Wybranie opcji etykietki narzędzia programu Visual Studio automatycznie tworzy metodę programu obsługi zdarzeń i kojarzy ją z zdarzenia w klasie publikowania.

Poniższy przykład przedstawia podstawowy wzorzec. `Windows::Foundation::TypedEventHandler` jest to typ delegata. Funkcja obsługi jest tworzony przy użyciu o nazwie funkcji.

W app.h:

[!code-cpp[cx_delegates#120](../cppcx/codesnippet/CPP/delegatesevents/class1.h#120)]

W app.cpp:

[!code-cpp[cx_delegates#121](../cppcx/codesnippet/CPP/delegatesevents/class1.cpp#121)]

> [!WARNING]
> Ogólnie rzecz biorąc procedury obsługi zdarzeń, lepiej jest używać o nazwie funkcji zamiast wyrażenia lambda, chyba że Zwróć szczególną uwagę aby uniknąć odwołania cykliczne. Funkcja o nazwie przechwytuje wskaźnik "this" przez słabe odwołanie, ale wyrażenie lambda przechwytuje go przez silne odwołanie i tworzy odwołanie cykliczne. Aby uzyskać więcej informacji, zobacz [słabe odwołania i przerywanie cykli](../cppcx/weak-references-and-breaking-cycles-c-cx.md).

Zgodnie z konwencją nazw delegata obsługi zdarzeń, które są definiowane przez środowisko wykonawcze Windows mają następującą formę * EventHandler — na przykład RoutedEventHandler, SizeChangedEventHandler lub SuspendingEventHandler. Ponadto zgodnie z Konwencją delegatów obsługi zdarzeń mają dwa parametry i zwracać typ void. Delegat, który nie ma parametrów typu, pierwszy parametr jest typu [Platform::Object ^](../cppcx/platform-object-class.md); posiada odwołanie do nadawcy, który jest obiektem, która wywołała zdarzenie. Masz rzutowanie do oryginalnego typu, zanim użyjesz argument w metodzie obsługi zdarzeń. W delegata obsługi zdarzeń, który ma parametry typu, pierwszy parametr typu określa typ nadawcy, a drugi parametr jest dojście do klasy referencyjnej, która przechowuje informacje o zdarzeniu. Zgodnie z Konwencją, ta klasa ma nazwę \*EventArgs. Na przykład obiekt delegowany RoutedEventHandler ma drugi parametr typu RoutedEventArgs ^, a drugi parametr typu DragEventArgs DragEventHander ^.

Zgodnie z Konwencją, są nazywane delegatów, które umieszczają w otoce kod, który jest wykonywany po zakończeniu operacji asynchronicznej * CompletedHandler. Te obiekty delegowane są definiowane jako właściwości klasy, nie jako zdarzeń. W związku z tym, nie używaj `+=` operator subskrybować; po prostu przypisać obiekt delegowany do właściwości.

> [!TIP]
> IntelliSense dla C++ nie wyświetla podpis delegata pełne; w związku z tym nie jest przydatne należy określić parametr EventArgs określonego typu. Aby znaleźć typ, możesz przejść do **przeglądarki obiektów** i przyjrzyj się `Invoke` metodę delegata.

## <a name="creating-custom-delegates"></a>Tworzenie niestandardowych delegatów

Można zdefiniować własne delegatów do definiowania programów obsługi zdarzeń lub zapewnienia konsumentów przekazać niestandardowe funkcje do składnika środowiska wykonawczego Windows. Podobnie jak dowolny inny typ środowiska uruchomieniowego Windows Delegat publiczny nie można zadeklarować jako ogólnego.

### <a name="declaration"></a>Deklaracja

Deklaracja delegata przypomina deklaracji funkcji, z tą różnicą, że delegat jest typem. Zazwyczaj można zadeklarować obiektu delegowany w zakresie przestrzeni nazw, chociaż można także zagnieżdżać deklaracja delegata w deklaracji klasy. Poniższy delegat hermetyzuje żadnej funkcji, która przyjmuje `ContactInfo^` jako dane wejściowe i zwraca `Platform::String^`.

[!code-cpp[cx_delegates#111](../cppcx/codesnippet/CPP/delegatesevents/class1.h#111)]

Po zadeklarowaniu typ delegata można zadeklarować składowych klasy tego typu lub metody, które przyjmują obiektów tego typu jako parametry. Metoda lub funkcja może również zwracać typ delegata. W poniższym przykładzie `ToCustomString` metoda przyjmuje delegata jako parametr wejściowy. Ta metoda umożliwia kodu klienta w celu umieszczenia niestandardowych funkcji, która tworzy ciąg z niektóre lub wszystkie publiczne właściwości `ContactInfo` obiektu.

[!code-cpp[Cx_delegates#112](../cppcx/codesnippet/CPP/delegatesevents/class1.h#112)]

> [!NOTE]
> Możesz użyć "^" symbol odwoływaniu się do typu delegata, tak samo, jak za pomocą dowolnego środowiska uruchomieniowego Windows odwołujesz typu.

Deklaracja zdarzenia są zawsze ma typ delegata. W tym przykładzie przedstawiono typowe delegatów podpis typu w środowisku uruchomieniowym Windows:

[!code-cpp[cx_delegates#122](../cppcx/codesnippet/CPP/delegatesevents/class1.h#122)]

`Click` Zdarzenia w `Windows:: UI::Xaml::Controls::Primitives::ButtonBase` klasy jest typu `RoutedEventHandler`. Aby uzyskać więcej informacji, zobacz [zdarzenia](../cppcx/events-c-cx.md).

Najpierw kod klienta tworzy wystąpienie delegata za pomocą `ref new` i zapewniając lambda, która jest zgodna z podpis delegata i definiuje niestandardowe zachowanie.

[!code-cpp[Cx_delegates#113](../cppcx/codesnippet/CPP/delegatesevents/class1.cpp#113)]

Następnie wywołuje funkcję elementu członkowskiego i przekazuje delegata. Przyjęto założenie, że `ci` jest `ContactInfo^` wystąpienia i `textBlock` jest XAML `TextBlock^`.

[!code-cpp[Cx_delegates#114](../cppcx/codesnippet/CPP/delegatesevents/class1.cpp#114)]

W następnym przykładzie aplikacja kliencka przekazuje niestandardową klasę delegatów do publicznej metody w składniku Windows Runtime, która wykonuje delegowanie dla każdej pozycji w `Vector`:

[!code-cpp[Cx_delegates#118](../cppcx/codesnippet/CPP/clientapp/mainpage.xaml.cpp#118)]

[!code-cpp[Cx_delegates#119](../cppcx/codesnippet/CPP/delegatesevents/class1.cpp#119)]

### <a name="construction"></a>Konstrukcja

Można utworzyć delegata z dowolnego z tych obiektów:

- lambda

- Funkcja statyczna

- wskaźnik do elementu członkowskiego

- STD::Function

Poniższy przykład przedstawia sposób tworzenia delegata z każdej z tych obiektów. Delegat będzie korzystać w taki sam sposób, bez względu na typ obiektu, który jest używany do tworzenia go.

[!code-cpp[Cx_delegates#115](../cppcx/codesnippet/CPP/delegatesevents/class1.cpp#115)]

> [!WARNING]
> Użycie wyrażenia lambda, która przechwytuje "to" wskaźnik, należy użyć `-=` operator, który ma być jawnie un rejestr ze zdarzenia przed zamknięciem wyrażenia lambda. Aby uzyskać więcej informacji, zobacz [zdarzenia](../cppcx/events-c-cx.md).

### <a name="generic-delegates"></a>Delegaty ogólne

Delegaty ogólne w C++/CX ma ograniczenia podobnych do deklaracji klasy ogólne. One nie można zadeklarować jako publiczne. Można zadeklarować prywatnego lub wewnętrznego ogólny delegować i używanie go z poziomu języka C++, ale .NET lub klientów języka JavaScript nie można pobrać go, ponieważ nie jest emitowany do metadanych .winmd. W tym przykładzie deklaruje Delegat ogólny, które mogą być używane tylko przez C++:

[!code-cpp[Cx_delegates#116](../cppcx/codesnippet/CPP/delegatesevents/class1.h#116)]

Następny przykład deklaruje specjalne wystąpienie delegata wewnątrz definicji klasy:

[!code-cpp[Cx_delegates#117](../cppcx/codesnippet/CPP/delegatesevents/class1.h#117)]

## <a name="delegates-and-threads"></a>Delegaci i wątki

Delegat, podobnie jak obiekt funkcji, zawiera kod, który zostanie wykonany w czasie w przyszłości. Jeśli kod, który tworzy i przekazuje delegata i funkcję, która akceptuje i wykonuje delegata, są uruchomione na tym samym wątku, czynności są stosunkowo proste. Jeśli wątek jest wątku interfejsu użytkownika, a następnie delegata bezpośrednio manipulować obiektów interfejsu użytkownika, takich jak kontrolki XAML.

Jeśli aplikacja kliencka ładuje składnika wykonawczego Windows działającą w komórek wielowątkowych i udostępnia delegata do tego składnika, następnie domyślnie obiekt delegowany jest wywoływany bezpośrednio w wątku STA. Większość składników środowiska wykonawczego Windows można uruchamiać w STA i MTA.

Jeśli kod, który wykonuje delegata jest uruchomiona w innym wątku — na przykład w kontekście obiektu concurrency::task — jesteś odpowiedzialny za synchronizowanie dostępu do udostępnionych danych. Na przykład jeśli pełnomocnik zawiera odwołanie do wektora, a kontrolki XAML odwołuje się do tego samego wektorowych, należy wykonać kroki w celu uniknięcia zakleszczenia lub sytuacje wyścigu, które mogą wystąpić podczas delegata i kontrolki XAML próbują uzyskać dostęp wektora na sam czas e. Użytkownik musi również powinien zachować ostrożność, delegat nie próbuje przechwycić według odwołań zmienne lokalne, które może być wykraczają poza zakres, zanim obiekt delegowany jest wywoływany.

Jeśli chcesz, aby Twoje utworzony delegat nastąpi wywołanie zwrotne w tym samym wątku, który został utworzony na — na przykład w przypadku przekazania składnik, który działa w komórce MTA — i można wywołać w tym samym wątku, jak twórca , następnie za pomocą przeciążenia konstruktora delegata, która przyjmuje sekundy `CallbackContext` parametru. To przeciążenie należy używać tylko w delegatów, które zostały zarejestrowane proxy/zastępczego; nie wszystkie delegatów, które są zdefiniowane w Windows.winmd są rejestrowane.

Osoby zaznajomione z programami obsługi zdarzeń w programie .NET wiesz, że zalecaną praktyką jest Utwórz lokalne kopie zdarzenia przed jej środowisko. Umożliwia to uniknięcie Sytuacje wyścigu, w których program obsługi zdarzeń mogą zostać usunięte przed zdarzenie jest wywoływane. Nie trzeba to zrobić w C++/CX ponieważ podczas dodawania lub usuwania programów obsługi zdarzeń zostanie utworzona nowa lista programu obsługi. Ponieważ obiektu języka C++ zwiększa liczbę odwołań na liście obsługi przed wywołaniem zdarzenia, jest gwarantowane, będzie obowiązywać wszystkich programów obsługi. Jednak oznacza to, że usunięcie procedury obsługi zdarzeń w zużywającym wątku tego wywołana procedura obsługi nieprawidłowego może nadal uzyskać Jeśli publikowania obiektu nadal działa na własną kopię listy, który jest obecnie przestarzałe. Obiekt publikowania nie otrzyma zaktualizowaną listę po ponownym jej generowane zdarzenie.

## <a name="see-also"></a>Zobacz także

[System typów](../cppcx/type-system-c-cx.md)<br/>
[Dokumentacja języka Visual C++](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[Dokumentacja przestrzeni nazw](../cppcx/namespaces-reference-c-cx.md)
