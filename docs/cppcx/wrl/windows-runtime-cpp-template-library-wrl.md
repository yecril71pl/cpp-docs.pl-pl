---
title: Biblioteka szablonów języka C++ środowiska wykonawczego systemu Windows (WRL)
ms.date: 11/04/2016
ms.topic: overview
ms.assetid: b915afce-553b-44a7-b8dc-0ab601758eb0
ms.openlocfilehash: b03dc98212bbc822ddc44871632fda73d1be8740
ms.sourcegitcommit: 6b3d793f0ef3bbb7eefaf9f372ba570fdfe61199
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/15/2020
ms.locfileid: "86404915"
---
# <a name="windows-runtime-c-template-library-wrl"></a>Biblioteka szablonów języka C++ środowiska wykonawczego systemu Windows (WRL)

Środowisko wykonawcze systemu Windows Biblioteka szablonów C++ (WRL) to Biblioteka szablonów, która zapewnia niskiego poziomu sposób tworzenia i używania składników środowisko wykonawcze systemu Windows.

> [!NOTE]
> WRL jest teraz zastępowany przez C++/WinRT, czyli standardową projekcją języka C++ 17 dla środowisko wykonawcze systemu Windows interfejsów API. C++/WinRT jest dostępna w zestawie SDK systemu Windows 10 w wersji 1803. Język C++/WinRT jest implementowany całkowicie w plikach nagłówkowych i zaprojektowany w celu zapewnienia pierwszej klasy dostępu do nowoczesnego interfejsu API systemu Windows.
>
> Za pomocą języka C++/WinRT można zarówno używać interfejsów API, jak i tworzyć ich środowisko wykonawcze systemu Windows za pomocą dowolnych zgodnych ze standardami kompilatorów języka C++ 17. C++/WinRT zazwyczaj wykonuje lepsze i tworzy mniejsze pliki binarne niż każda inna opcja języka dla środowisko wykonawcze systemu Windows. Będziemy nadal obsługiwać C++/CX i WRL, ale zdecydowanie zaleca się, aby nowe aplikacje korzystały z języka C++/WinRT. Aby uzyskać więcej informacji, zobacz [C++/WinRT](https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/index).

## <a name="benefits"></a>Korzyści

Środowisko wykonawcze systemu Windows Biblioteka szablonów C++ umożliwia łatwiejsze wdrażanie i używanie składników Component Object Model (COM). Zapewnia to metody dla gospodarstw domowych, takie jak zliczanie odwołań do zarządzania okresem istnienia obiektów i testowaniem wartości HRESULT, w celu określenia, czy operacja zakończyła się powodzeniem, czy niepowodzeniem. Aby pomyślnie korzystać z biblioteki szablonów języka środowisko wykonawcze systemu Windows C++, należy uważnie przestrzegać tych zasad i technik.

C++/CX to ogólny, oparty na języku sposób używania składników środowisko wykonawcze systemu Windows. Zarówno Biblioteka szablonów C++ środowisko wykonawcze systemu Windows, jak i C++/CX upraszczają pisanie kodu dla środowisko wykonawcze systemu Windows przez automatyczne wykonywanie zadań dla gospodarstw domowych w Twoim imieniu.

Biblioteka szablonów C++ środowisko wykonawcze systemu Windows i C++/CX zapewniają różne korzyści. Oto kilka powodów, dla których warto środowisko wykonawcze systemu Windows użyć biblioteki szablonów języka C++/CX zamiast języka C++:

- Środowisko wykonawcze systemu Windows Biblioteka szablonów C++ dodaje niewielki abstrakcję za pośrednictwem interfejsu binarnego środowisko wykonawcze systemu Windows aplikacji (ABI), co daje możliwość kontrolowania bazowego kodu w celu lepszego tworzenia lub używania środowisko wykonawcze systemu Windows interfejsów API.

- C++/CX reprezentuje wartości HRESULT modelu COM jako wyjątki. Jeśli została dziedziczona baza kodu, która używa modelu COM lub taka, która nie korzysta z wyjątków, może się okazać, że środowisko wykonawcze systemu Windows Biblioteka szablonów C++ jest bardziej naturalnym sposobem pracy z środowisko wykonawcze systemu Windows, ponieważ nie trzeba używać wyjątków.

   > [!NOTE]
   > Biblioteka szablonów języka C++ środowisko wykonawcze systemu Windows używa wartości HRESULT i nie generuje wyjątków. Ponadto Biblioteka szablonów języka C++ środowisko wykonawcze systemu Windows korzysta z inteligentnych wskaźników i wzorca RAII, aby pomóc zagwarantować, że obiekty są poprawnie niszczone, gdy kod aplikacji zgłasza wyjątek. Aby uzyskać więcej informacji na temat inteligentnych wskaźników i RAII, zobacz [inteligentne wskaźniki](../../cpp/smart-pointers-modern-cpp.md) i [obiekty własne (RAII)](../../cpp/objects-own-resources-raii.md).

- Cel i projekt biblioteki szablonów w języku środowisko wykonawcze systemu Windows C++ są inspirowane Active Template Library (ATL), czyli zestawem klas C++ opartych na szablonach, które upraszczają programowanie obiektów COM. Ponieważ Biblioteka szablonów C++ środowisko wykonawcze systemu Windows używa standardowego języka C++ do zawijania środowisko wykonawcze systemu Windows, można łatwiej portować i korzystać z wielu istniejących składników COM, które są zapisywane w ATL, do środowisko wykonawcze systemu Windows. Jeśli znasz już ATL, może się okazać, że programowanie biblioteki szablonów w języku C++ środowisko wykonawcze systemu Windows jest łatwiejsze.

## <a name="getting-started"></a>Getting Started

Poniżej przedstawiono niektóre zasoby, które mogą pomóc w rozpoczęciu pracy z biblioteką szablonów języka C++ środowisko wykonawcze systemu Windows.

[Biblioteka środowisko wykonawcze systemu Windows (WRL)](https://channel9.msdn.com/Events/Windows-Camp/Developing-Windows-8-Metro-style-apps-in-Cpp/The-Windows-Runtime-Library-WRL-)<br/>
W tym wideo kanału Channel 9 dowiesz się więcej o tym, jak Biblioteka szablonów C++ środowisko wykonawcze systemu Windows ułatwia pisanie aplikacji platforma uniwersalna systemu Windows (platformy UWP) oraz sposób tworzenia i używania składników środowisko wykonawcze systemu Windows.

[Instrukcje: aktywowanie i używanie składnika środowisko wykonawcze systemu Windows](how-to-activate-and-use-a-windows-runtime-component-using-wrl.md)<br/>
Pokazuje, w jaki sposób używać środowisko wykonawcze systemu Windows biblioteki szablonów C++ do inicjowania środowisko wykonawcze systemu Windows i aktywowania i używania składnika środowisko wykonawcze systemu Windows.

[Instrukcje: Kończenie operacji asynchronicznych](how-to-complete-asynchronous-operations-using-wrl.md)<br/>
Pokazuje, jak używać biblioteki szablonów języka C++ środowisko wykonawcze systemu Windows do uruchamiania operacji asynchronicznych i wykonywania pracy po zakończeniu operacji.

[Instrukcje: obsługa zdarzeń](how-to-handle-events-using-wrl.md)<br/>
Pokazuje, jak używać biblioteki szablonów języka C++ środowisko wykonawcze systemu Windows, aby subskrybować i obsłużyć zdarzenia środowisko wykonawcze systemu Windows obiektu.

[Przewodnik: Tworzenie aplikacji platformy uniwersalnej systemu Windows z użyciem biblioteki WRL i platformy Media Foundation](walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation.md)<br/>
Dowiedz się, jak utworzyć aplikację platformy UWP, która używa [Microsoft Media Foundation](/windows/win32/medfound/microsoft-media-foundation-sdk).

[Instrukcje: tworzenie klasycznego składnika COM](how-to-create-a-classic-com-component-using-wrl.md)<br/>
Pokazuje, jak używać biblioteki szablonów języka C++ środowisko wykonawcze systemu Windows do tworzenia podstawowego składnika modelu COM i podstawowego sposobu rejestrowania i używania składnika COM z poziomu aplikacji klasycznej.

[Instrukcje: Tworzenie wystąpień WRL składników bezpośrednio](how-to-instantiate-wrl-components-directly.md)<br/>
Dowiedz się, jak używać funkcji [Microsoft:: WRL:: Make](make-function.md) i [Microsoft:: WRL::D etails:: MakeAndInitialize](makeandinitialize-function.md) , aby utworzyć wystąpienie składnika z modułu, który go definiuje.

[Instrukcje: Użycie winmdidl.exe i midlrt.exe w celu utworzenia plików .h z metadanych systemu Windows](use-winmdidl-and-midlrt-to-create-h-files-from-windows-metadata.md)<br/>
Pokazuje, jak używać niestandardowych składników środowisko wykonawcze systemu Windows z WRL przez utworzenie pliku IDL z metadanych. winmd.

[Wskazówki: łączenie za pomocą zadań i żądań HTTP XML](../../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md)<br/>
Pokazuje, w jaki sposób używać interfejsów [IXMLHTTPRequest2](/windows/win32/api/msxml6/nn-msxml6-ixmlhttprequest2) i [IXMLHTTPRequest2Callback](/windows/win32/api/msxml6/nn-msxml6-ixmlhttprequest2callback) wraz z zadaniami do wysyłania żądań HTTP GET i post do usługi sieci Web w aplikacji platformy UWP.

[Przykład Optymalizatora podróży w usłudze mapy Bing](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples)<br/>
Używa `HttpRequest` klasy, która jest zdefiniowana w [instruktażu: łączenie za pomocą zadań i żądań HTTP XML](../../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md) w kontekście kompletnej aplikacji platformy UWP.

[Tworzenie składnika DLL środowisko wykonawcze systemu Windows za pomocą przykładu C++](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples)<br/>
Pokazuje, jak używać biblioteki szablonów języka C++ środowisko wykonawcze systemu Windows do tworzenia składnika biblioteki DLL w procesie i korzystania z niego z C++/CX, JavaScript i C#.

[Przykładowa gra DirectX marmur labiryntu](https://docs.microsoft.com/samples/microsoft/windows-appsample-marble-maze/directx-marble-maze-game-sample/)<br/>
Pokazuje, jak używać biblioteki szablonów języka C++ środowisko wykonawcze systemu Windows do zarządzania okresem istnienia składników COM, takich jak DirectX i platforma Media Foundation, w kontekście kompletnej gry trójwymiarowej.

[Wyskakujące powiadomienia z aplikacji klasycznych](/windows/uwp/design/shell/tiles-and-notifications/toast-desktop-apps)<br/>
Pokazuje, jak wysyłać wyskakujące powiadomienia z aplikacji klasycznej.

## <a name="windows-runtime-c-template-library-compared-to-atl"></a>Biblioteka szablonów języka C++ środowisko wykonawcze systemu Windows w porównaniu do ATL

Biblioteka szablonów C++ środowisko wykonawcze systemu Windows jest podobna do Active Template Library (ATL), ponieważ można jej użyć do tworzenia małych i szybkich obiektów COM. Środowisko wykonawcze systemu Windows biblioteki szablonów C++ i ATL również współdzielą pojęcia, takie jak definicja obiektów w modułach, jawna Rejestracja interfejsów i otwieranie obiektów przy użyciu fabryk. Znajomość biblioteki szablonów języka C++ środowisko wykonawcze systemu Windows może być wygodna w przypadku korzystania z ATL.

Biblioteka szablonów języka C++ środowisko wykonawcze systemu Windows obsługuje funkcje COM wymagane przez aplikacje platformy UWP. W związku z tym różni się od ATL, ponieważ pomija bezpośrednią obsługę funkcji COM, takich jak:

- Agregacja

- implementacje giełdowe

- podwójne interfejsy ( `IDispatch` )

- standardowe interfejsy modułu wyliczającego

- punkty połączenia

- interfejsy odrywające

- Osadzanie OLE

- ActiveX — formanty

- COM+

## <a name="concepts"></a>Pojęcia

Środowisko wykonawcze systemu Windows Biblioteka szablonów C++ zawiera typy, które reprezentują kilka podstawowych pojęć. W poniższych sekcjach opisano te typy.

### <a name="comptr"></a>ComPtr

[ComPtr](comptr-class.md) to *inteligentny typ wskaźnika* , który reprezentuje interfejs, który jest określony przez parametr szablonu. Użyj `ComPtr` , aby zadeklarować zmienną, która może uzyskać dostęp do elementów członkowskich obiektu, który pochodzi z interfejsu. `ComPtr`automatycznie utrzymuje liczbę odwołań dla wskaźnika źródłowego i zwalnia interfejs, gdy liczba odwołań spadnie do zera.

### <a name="runtimeclass"></a>RuntimeClass

[RuntimeClass](runtimeclass-class.md) reprezentuje klasę skonkretyzowany, która dziedziczy zestaw określonych interfejsów. `RuntimeClass`Obiekt może zapewnić kombinację obsługi jednego lub wielu środowisko wykonawcze systemu Windows interfejsów com lub słabe odwołanie do składnika.

### <a name="module"></a>Moduł

[Moduł](module-class.md) reprezentuje kolekcję obiektów pokrewnych. `Module`Obiekt zarządza fabrykami klas, które tworzą obiekty i rejestrację, co umożliwia innym aplikacjom korzystanie z obiektu.

### <a name="callback"></a>Wywołania zwrotnego

Funkcja [wywołania zwrotnego](callback-function-wrl.md) tworzy obiekt, którego funkcja członkowska jest procedurą obsługi zdarzeń (metoda wywołania zwrotnego). Użyj `Callback` funkcji do zapisywania operacji asynchronicznych.

### <a name="eventsource"></a>EventSource

Element [EventSource](eventsource-class.md) służy do zarządzania obsługą zdarzeń *delegatów* . Użyj środowisko wykonawcze systemu Windows biblioteki szablonów C++, aby zaimplementować delegata, i użyć `EventSource` do dodawania, usuwania i wywoływania delegatów.

### <a name="asyncbase"></a>AsyncBase

[AsyncBase](asyncbase-class.md) udostępnia metody wirtualne, które reprezentują model programowania asynchronicznego środowisko wykonawcze systemu Windows. Przesłoń składowe w tej klasie, aby utworzyć klasę niestandardową, która może uruchamiać, zatrzymywać lub sprawdzać postęp operacji asynchronicznej.

### <a name="ftmbase"></a>FtmBase

[FtmBase](ftmbase-class.md) reprezentuje obiekt marshaler o dowolnym wątku. `FtmBase`tworzy globalną tabelę interfejsów (GIT) i pomaga zarządzać kierowaniem obiektów i obiektami proxy.

### <a name="weakref"></a>WeakRef

[WeakRef](weakref-class.md) jest typem wskaźnika inteligentnego, który reprezentuje *słabe odwołanie*, które odwołuje się do obiektu, który może lub być niedostępny. `WeakRef`Obiekt może być używany tylko przez środowisko wykonawcze systemu Windows, a nie za pomocą klasycznego modelu com.

`WeakRef`Obiekt zazwyczaj reprezentuje obiekt, którego istnienie jest kontrolowane przez zewnętrzny wątek lub aplikację. Na przykład `WeakRef` obiekt może odwoływać się do obiektu pliku. Gdy plik jest otwarty, `WeakRef` jest prawidłowy i dostępny jest plik, do którego się odwołuje. Ale gdy plik jest zamknięty, `WeakRef` jest nieprawidłowy, a plik jest niedostępny.

## <a name="related-topics"></a>Tematy pokrewne

|||
|-|-|
|[Najważniejsze interfejsy API według kategorii](key-wrl-apis-by-category.md)|Podświetla podstawowe typy bibliotek szablonów języka C++, funkcje i makra środowisko wykonawcze systemu Windows.|
|[Tematy pomocy](wrl-reference.md)|Zawiera informacje referencyjne dla biblioteki szablonów środowisko wykonawcze systemu Windows C++.|
|[Krótki przewodnik (C++/CX)](../../cppcx/quick-reference-c-cx.md)|Zwięźle opisuje funkcje języka C++/CX, które obsługują środowisko wykonawcze systemu Windows.|
|[Używanie składników środowisko wykonawcze systemu Windows w Visual C++](/windows/uwp/winrt-components/walkthrough-creating-a-basic-windows-runtime-component-in-cpp-and-calling-it-from-javascript-or-csharp)|Pokazuje, jak utworzyć podstawowy składnik środowisko wykonawcze systemu Windows przy użyciu języka C++/CX.|
