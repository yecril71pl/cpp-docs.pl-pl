---
title: Delegaty (C + +/ CX) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/22/2017
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3175bf1c-86d8-4eda-8d8f-c5b6753d8e38
caps.latest.revision: "30"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.openlocfilehash: dee99cf85ff47fe7dbde8bd8bc7f60f708a5ebc6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="delegates-ccx"></a>Delegaty (C + +/ CX)
`delegate` — Słowo kluczowe służy do deklarowania typu odwołania, który jest odpowiednikiem obiektem funkcji w standardu C++ środowiska wykonawczego systemu Windows. Deklaracji obiektu delegowanego podobne do podpisu funkcji. Określa typ zwracany i typy parametrów, które muszą mieć jego opakowana funkcja. Jest to deklaracji obiektu delegowanego zdefiniowane przez użytkownika:  
  
```cpp  
     public delegate void PrimeFoundHandler(int result);  
```  
  
 Obiekty delegowane są najczęściej używane w połączeniu ze zdarzeniami. Zdarzenie ma typem obiektu delegowanego w taki sam sposób, że klasa może mieć typu interfejsu. Delegat reprezentuje kontraktu, który znacznie wykonania procedury obsługi zdarzeń. W tym miejscu jest element członkowski klasy zdarzenie, którego typ to uprzednio zdefiniowany delegata:  
  
```cpp  
event PrimeFoundHandler^ primeFoundEvent;  
```  
  
 Przy deklarowaniu obiektów delegowanych, które mają być widoczne dla klientów przez binarny interfejsu środowiska wykonawczego systemu Windows, użyj [Windows::Foundation::TypedEventHandler\<TSender, TResult >](http://msdn.microsoft.com/library/windows/apps/br225997.aspx). Ten delegat ma wstępnie zdefiniowane ustawienia serwera proxy i stub pliki binarne mogła być używane przez klientów języka Javascript.  
  
## <a name="consuming-delegates"></a>Korzystanie z obiektów delegowanych  
 Podczas tworzenia aplikacji platformy uniwersalnej systemu Windows często pracować z delegatem, jako typ zdarzenia, które udostępnia klasy środowiska wykonawczego systemu Windows. Aby subskrybować zdarzenia, należy utworzyć wystąpienia jego typ delegowany, określając funkcję — lub lambda — odpowiadającego podpisu delegata. Następnie użyj `+=` operatora, aby przekazać obiektu delegowanego z elementem członkowskim zdarzenia w klasie. Jest to nazywane subskrybowanie zdarzeń. Gdy wystąpienie klasy "generowane" zdarzenia, funkcja jest wywoływana oraz innych programów obsługi, które zostały dodane przez nazwę obiektu lub inne obiekty.  
  
> [!TIP]
>  Program Visual Studio jest dużo pracy podczas tworzenia program obsługi zdarzeń. Na przykład jeśli określisz program obsługi zdarzeń w kodzie XAML, pojawi się etykietka narzędzia. Jeśli wybierzesz etykietka narzędzia Visual Studio automatycznie tworzy metoda obsługi zdarzeń i kojarzy ją z zdarzenia w klasie publikowania.  
  
 W poniższym przykładzie przedstawiono podstawowe wzorca. `Windows::Foundation::TypedEventHandler`jest to typ delegata. Funkcja obsługi jest tworzony przy użyciu funkcji o nazwie.  
  
 W app.h:  
  
 [!code-cpp[cx_delegates#120](../cppcx/codesnippet/CPP/delegatesevents/class1.h#120)]  
  
 W app.cpp:  
  
 [!code-cpp[cx_delegates#121](../cppcx/codesnippet/CPP/delegatesevents/class1.cpp#121)]  
  
> [!WARNING]
>  Ogólnie rzecz biorąc dla programu obsługi zdarzeń, warto użyć funkcji o nazwie zamiast wyrażenia lambda, chyba że zostanie zastosowane szczególną uwagę, aby uniknąć odwołań cyklicznych. Funkcja o nazwie przechwytuje wskaźnik "this" przez odwołanie słabe, ale wyrażenie lambda przechwytuje go przez silne odwołanie i tworzy odwołanie cykliczne. Aby uzyskać więcej informacji, zobacz [słabe odwołania i cykle podziału](../cppcx/weak-references-and-breaking-cycles-c-cx.md).  
  
 Konwencja, nazwy obiektu delegowanego obsługi zdarzeń, które są definiowane przez środowisko wykonawcze systemu Windows mają następującą postać * EventHandler — na przykład RoutedEventHandler, SizeChangedEventHandler lub SuspendingEventHandler. Również w Konwencji, delegatów obsługi zdarzeń ma dwa parametry i zwracać typ void. W elemencie delegowanym, który nie ma parametrów typu, pierwszy parametr jest typu [Platform::Object ^](../cppcx/platform-object-class.md); posiada odwołanie do nadawcy, który jest obiektem spowodowało wyzwolenie zdarzenia. Należy rzutować wstecz do oryginalnego typu przed użyciem argument w metoda obsługi zdarzeń. W elemencie delegowanym programu obsługi zdarzeń, który ma parametry typu, pierwszy parametr typu określa typ nadawcy, a drugi parametr jest dojście do klasy ref, która przechowuje informacje o zdarzeniu. Według Konwencji tej klasy, nosi \*EventArgs. Na przykład delegata RoutedEventHandler ma drugi parametr typu RoutedEventArgs ^, a drugi parametr typu DragEventArgs ma DragEventHander ^.  
  
 Według Konwencji o nazwie delegatów, które otaczają kod, który jest wykonywany po zakończeniu operacji asynchronicznej * CompletedHandler. Te obiekty delegowane są definiowane jako właściwości klasy, nie jako zdarzenia. W związku z tym nie używaj `+=` operatora, aby subskrybować; obiektu delegowanego tylko przypisać do właściwości.  
  
> [!TIP]
>  IntelliSense dla C++ nie wyświetla podpisu delegata pełne; w związku z tym go nie pomóc w określeniu określonego typu parametr EventArgs. Można znaleźć typu, możesz przejść do **przeglądarki obiektów** i przyjrzyj się `Invoke` metoda obiektu delegowanego.  
  
## <a name="creating-custom-delegates"></a>Tworzenie niestandardowych delegatów  
 Możesz definiować własne delegatów, zdefiniuj programy obsługi zdarzeń lub włączyć konsumentów do przekazania w funkcji niestandardowych do składnika środowiska wykonawczego systemu Windows. Innych typów środowiska wykonawczego systemu Windows Delegat publiczny nie można zadeklarować jako ogólnego.  
  
### <a name="declaration"></a>Deklaracja  
 Deklaracja delegata podobny deklaracji funkcji, z wyjątkiem tego, że delegat jest typem. Zazwyczaj deklarowaniu delegata w zakresie przestrzeni nazw, chociaż można zagnieżdżać w deklaracji obiektu delegowanego w deklaracji klasy. Następujące delegata hermetyzuje dowolnej funkcji, która przyjmuje `ContactInfo^` jako dane wejściowe i zwraca `Platform::String^`.  
  
 [!code-cpp[cx_delegates#111](../cppcx/codesnippet/CPP/delegatesevents/class1.h#111)]  
  
 Po deklaracji typu delegata można zadeklarować elementów członkowskich klasy tego typu lub metody, które przyjmują obiekty tego typu jako parametry. Metody lub funkcji również może zwracać typ obiektu delegowanego. W poniższym przykładzie `ToCustomString` metoda przyjmuje delegata jako parametr wejściowy. Ta metoda umożliwia kodu klienta w celu umieszczenia niestandardowej funkcji, która tworzy ciąg z niektórych lub wszystkich publicznych właściwości `ContactInfo` obiektu.  
  
 [!code-cpp[Cx_delegates#112](../cppcx/codesnippet/CPP/delegatesevents/class1.h#112)]  
  
> [!NOTE]
>  Możesz użyć "^" symboli w przypadku odwoływania się do typu delegowanego tak samo, jak możesz z dowolnego środowiska wykonawczego systemu Windows zawierają odwołania do typu.  
  
 Deklaracja zdarzenia są zawsze ma typ delegata. W tym przykładzie przedstawiono typowe delegata podpis typu w środowisku wykonawczym systemu Windows:  
  
 [!code-cpp[cx_delegates#122](../cppcx/codesnippet/CPP/delegatesevents/class1.h#122)]  
  
 `Click` Zdarzenia w `Windows:: UI::Xaml::Controls::Primitives::ButtonBase` klasy jest typu `RoutedEventHandler`. Aby uzyskać więcej informacji, zobacz [zdarzenia](../cppcx/events-c-cx.md).  
  
 Kod klienta najpierw tworzy wystąpienie obiektu delegowanego przy użyciu `ref new` i Wyrażenie lambda jest zgodny z podpisu delegata, który definiuje niestandardowe zachowanie.  
  
 [!code-cpp[Cx_delegates#113](../cppcx/codesnippet/CPP/delegatesevents/class1.cpp#113)]  
  
 Następnie wywołuje funkcję elementu członkowskiego i przekazuje obiekt delegowany. Przyjęto założenie, że `ci` jest `ContactInfo^` wystąpienia i `textBlock` jest XAML `TextBlock^`.  
  
 [!code-cpp[Cx_delegates#114](../cppcx/codesnippet/CPP/delegatesevents/class1.cpp#114)]  
  
 W następnym przykładzie aplikacja kliencka przekazuje niestandardowych delegata publiczną metodę składnika środowiska wykonawczego systemu Windows, która wykonuje delegowanie dla każdej pozycji w `Vector`:  
  
 [!code-cpp[Cx_delegates#118](../cppcx/codesnippet/CPP/clientapp/mainpage.xaml.cpp#118)]  
  
 [!code-cpp[Cx_delegates#119](../cppcx/codesnippet/CPP/delegatesevents/class1.cpp#119)]  
  
### <a name="construction"></a>Konstrukcji  
 Można utworzyć delegata z dowolnego z tych obiektów:  
  
-   lambda  
  
-   Funkcja statyczna  
  
-   wskaźnik do elementu członkowskiego  
  
-   STD::Function  
  
 Poniższy przykład przedstawia sposób tworzenia delegata z każdej z tych obiektów. Delegat można korzystać w taki sam sposób, bez względu na typ obiektu, który jest używany do tworzenia go.  
  
 [!code-cpp[Cx_delegates#115](../cppcx/codesnippet/CPP/delegatesevents/class1.cpp#115)]  
  
> [!WARNING]
>  Jeśli używasz lambda, która przechwytuje wskaźnik "this", należy użyć `-=` operatora, aby jawnie wyrejestrować ze zdarzenia przed zakończeniem pracy lambda. Aby uzyskać więcej informacji, zobacz [zdarzenia](../cppcx/events-c-cx.md).  
  
### <a name="generic-delegates"></a>Delegaty ogólne  
 Delegaty ogólne w języku C + +/ CX mają podobne do deklaracji klasy ogólne ograniczenia. Ich nie można zadeklarować jako publiczną. Można zadeklarować prywatnej lub rodzajowa wewnętrzny delegować i pobrać go z C++, ale .NET lub klientów języka JavaScript nie można pobrać go, ponieważ nie jest emitowany do metadanych winmd. W tym przykładzie deklaruje Delegat ogólny, które mogą być używane tylko przez C++:  
  
 [!code-cpp[Cx_delegates#116](../cppcx/codesnippet/CPP/delegatesevents/class1.h#116)]  
  
 Kolejnym przykładzie deklaruje specjalne wystąpienie klasy delegata wewnątrz definicji klasy:  
  
 [!code-cpp[Cx_delegates#117](../cppcx/codesnippet/CPP/delegatesevents/class1.h#117)]  
  
## <a name="delegates-and-threads"></a>Delegaci i wątków  
 Delegat, podobnie jak obiektem funkcji zawiera kod, który zostanie wykonany w czasie w przyszłości. Jeśli kod, który tworzy i przekazuje delegata i funkcję, która akceptuje i wykonuje delegata, są uruchomione na tym samym wątku, elementy są stosunkowo proste. Wątek jest wątku interfejsu użytkownika, a następnie Delegat może bezpośrednio operować obiekty interfejsu użytkownika, takie jak kontrolki XAML.  
  
 Jeśli aplikacja kliencka ładuje składnika środowiska wykonawczego systemu Windows działającą w komórek wielowątkowych i udostępnia delegata do tego składnika, następnie domyślnie delegat jest wywoływana bezpośrednio w wątku STA. Większość składników środowiska wykonawczego systemu Windows można uruchamiać w STA i MTA.  
  
 Jeśli kod, który wykonuje delegat jest uruchomiona w innym wątku — na przykład w kontekście obiektu concurrency::task — a następnie jest odpowiedzialny za synchronizowanie dostępu do udostępnionych danych. Na przykład jeśli pełnomocnika zawiera odwołanie do wektora i kontrolki XAML odwołuje się do tego samego wektora, należy wykonać czynności, aby uniknąć zakleszczenie lub wyścigu, które mogą wystąpić przy próbie dostępu wektor pod sam zarówno delegata i kontrolki XAML czas e. Należy również rozwiązywane delegat nie próbować przechwytywanie przez odwołanie zmienne lokalne, które mogą się znaleźć poza zakresem przed jest wywoływany delegat.  
  
 Jeśli chcesz, aby utworzony pełnomocnik ma być wywołanie zwrotne w tym samym wątku, który został utworzony na — na przykład w przypadku przekazania składnik, który działa w komórce MTA — i chcesz je do wywołania w tym samym wątku, co twórca , następnie użyć przeładowania konstruktora delegata pobierającej drugiej `CallbackContext` parametru. To przeciążenie należy używać tylko delegatów mających zarejestrowanego serwera proxy/stub; nie wszystkie delegatów, które są zdefiniowane w plik Windows.winmd jest zarejestrowany.  
  
 Jeśli znasz obsługi zdarzeń w .NET wiesz, czy zalecaną praktyką jest utworzyć lokalnej kopii zdarzenia przed jego uruchomienie. Dzięki temu można uniknąć wyścigu, w których program obsługi zdarzeń mogą zostać usunięte przed zdarzenie jest wywoływane. Nie trzeba to zrobić w języku C + +/ CX ponieważ podczas dodawania lub usuwania programów obsługi zdarzeń jest utworzona nowa lista programu obsługi. Ponieważ obiekt C++ zwiększa liczbę odwołania na liście obsługi przed wywołaniem zdarzenia, będzie obowiązywać wszystkich programów obsługi jest gwarantowana. Jednakże oznacza to też, że po usunięciu program obsługi zdarzeń w wątku odbierającą programu obsługi może nadal uzyskać wywoływane, jeśli nadal działa publikowania obiektu w jego kopię na liście, który jest teraz przestarzałe. Obiekt publikowania nie otrzyma zaktualizowanej listy do czasu jej generowane zdarzenie.  
  
## <a name="see-also"></a>Zobacz też  
 [System typów](../cppcx/type-system-c-cx.md)   
 [Dokumentacja języka Visual C++](../cppcx/visual-c-language-reference-c-cx.md)   
 [Odwołanie do przestrzeni nazw](../cppcx/namespaces-reference-c-cx.md)