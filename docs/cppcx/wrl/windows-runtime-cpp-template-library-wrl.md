---
title: Biblioteka szablonów języka C++ środowiska wykonawczego systemu Windows (WRL)
ms.date: 11/04/2016
ms.topic: landing-page
ms.assetid: b915afce-553b-44a7-b8dc-0ab601758eb0
ms.openlocfilehash: 7a92676d198ed9ddffeae9a834ebd358c2c58e90
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70740842"
---
# <a name="windows-runtime-c-template-library-wrl"></a>Biblioteka szablonów języka C++ środowiska wykonawczego systemu Windows (WRL)

Biblioteka szablonów C++ środowisko wykonawcze systemu Windows (WRL) to Biblioteka szablonów, która zapewnia niskiego poziomu sposób tworzenia i używania składników Środowisko wykonawcze systemu Windows.

> [!NOTE]
> WRL jest teraz zastępowany przez C++/WinRT, czyli standardowego języka c++ 17 dla środowisko wykonawcze systemu Windows interfejsów API. C++/WinRT jest dostępny w zestawie SDK systemu Windows 10 w wersji 1803. C++/WinRT jest zaimplementowana całkowicie w plikach nagłówkowych i zaprojektowana w celu zapewnienia pierwszej klasy dostępu do nowoczesnego interfejsu API systemu Windows.
>
> Dzięki C++/WinRT można korzystać z interfejsów api i środowisko wykonawcze systemu Windows tworzyć je za pomocą dowolnych zgodnych ze standardami kompilatorów języka c++ 17. C++/WinRT zazwyczaj wykonuje lepsze i produkuje mniejsze pliki binarne niż każda inna opcja języka dla środowisko wykonawcze systemu Windows. Będziemy nadal obsługiwać C++/CX i WRL, ale zdecydowanie zaleca się, aby nowe aplikacje korzystały C++z/WinRT. Aby uzyskać więcej informacji, zobacz [ C++/WinRT](https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/index).

## <a name="benefits"></a>Zalety

Biblioteka szablonów C++ środowisko wykonawcze systemu Windows umożliwia łatwiejsze wdrażanie i zużywanie składników Component Object Model (com). Zapewnia to metody dla gospodarstw domowych, takie jak zliczanie odwołań do zarządzania okresem istnienia obiektów i testowaniem wartości HRESULT, w celu określenia, czy operacja zakończyła się powodzeniem, czy niepowodzeniem. Aby pomyślnie korzystać z biblioteki C++ szablonów środowisko wykonawcze systemu Windows, należy uważnie przestrzegać tych zasad i technik.

C++/CX to oparty na języku sposób, który umożliwia korzystanie ze składników Środowisko wykonawcze systemu Windows. Zarówno Biblioteka szablonów C++ środowisko wykonawcze systemu Windows, jak C++i/CX upraszczają pisanie kodu dla środowisko wykonawcze systemu Windows przez automatyczne wykonywanie zadań dla gospodarstw domowych w Twoim imieniu.

Biblioteka szablonów C++ środowisko wykonawcze systemu Windows i C++/CX zapewniają różne korzyści. Oto kilka powodów, dla których warto użyć biblioteki szablonów środowisko wykonawcze systemu Windows C++ zamiast C++/CX:

- Biblioteka C++ szablonów środowisko wykonawcze systemu Windows dodaje niewielki abstrakcję za pośrednictwem interfejsu binarnego środowisko wykonawcze systemu Windows aplikacji (ABI), co umożliwia kontrolowanie kodu bazowego w celu lepszego tworzenia lub używania środowisko wykonawcze systemu Windows interfejsów API.

- C++/CX reprezentuje wartości HRESULT modelu COM jako wyjątki. Jeśli została dziedziczona baza kodu, która używa modelu COM lub taka, która nie korzysta z wyjątków, może się okazać, że C++ środowisko wykonawcze systemu Windows Biblioteka szablonów jest bardziej naturalnym sposobem pracy z środowisko wykonawcze systemu Windows, ponieważ nie trzeba używać wyjątków.

   > [!NOTE]
   > Biblioteka szablonów C++ środowisko wykonawcze systemu Windows używa wartości HRESULT i nie generuje wyjątków. Ponadto Biblioteka szablonów środowisko wykonawcze systemu Windows C++ używa inteligentnych wskaźników i wzorca RAII, aby pomóc w zapewnieniu, że obiekty są poprawnie niszczone, gdy kod aplikacji zgłasza wyjątek. Aby uzyskać więcej informacji na temat inteligentnych wskaźników i RAII, zobacz [inteligentne wskaźniki](../../cpp/smart-pointers-modern-cpp.md) i [obiekty własne (RAII)](../../cpp/objects-own-resources-raii.md).

- Projektowanie środowisko wykonawcze systemu Windows C++ szablonów jest inspirowane Active Template Library (ATL), który jest zestawem klas opartych na C++ szablonach, które upraszczają programowanie obiektów com. Ponieważ biblioteka C++ szablonów środowisko wykonawcze systemu Windows używa standardu C++ do zawijania środowisko wykonawcze systemu Windows, można łatwiej portować i korzystać z wielu istniejących składników com, które są zapisywane w ATL, do środowisko wykonawcze systemu Windows. Jeśli znasz już ATL, może się okazać, że programowanie C++ biblioteki szablonów środowisko wykonawcze systemu Windows jest łatwiejsze.

## <a name="getting-started"></a>Wprowadzenie

Poniżej przedstawiono niektóre zasoby, które mogą pomóc w rozpoczęciu pracy C++ z biblioteką szablonów środowisko wykonawcze systemu Windows.

[Biblioteka środowisko wykonawcze systemu Windows (WRL)](https://channel9.msdn.com/Events/Windows-Camp/Developing-Windows-8-Metro-style-apps-in-Cpp/The-Windows-Runtime-Library-WRL-)<br/>
W tym filmie wideo kanału 9 dowiesz się więcej o tym C++ , jak biblioteka szablonów środowisko wykonawcze systemu Windows ułatwia pisanie aplikacji platforma uniwersalna systemu Windows (platformy UWP) oraz sposób tworzenia i używania składników Środowisko wykonawcze systemu Windows.

[Instrukcje: Aktywowanie i używanie składnika środowisko wykonawcze systemu Windows](how-to-activate-and-use-a-windows-runtime-component-using-wrl.md)<br/>
Pokazuje, w jaki sposób używać C++ środowisko wykonawcze systemu Windows biblioteki szablonów do inicjowania środowisko wykonawcze systemu Windows i aktywowania i używania składnika Środowisko wykonawcze systemu Windows.

[Instrukcje: Ukończ operacje asynchroniczne](how-to-complete-asynchronous-operations-using-wrl.md)<br/>
Pokazuje, jak używać biblioteki szablonów C++ środowisko wykonawcze systemu Windows do uruchamiania operacji asynchronicznych i wykonywania pracy po zakończeniu operacji.

[Instrukcje: Obsługa zdarzeń](how-to-handle-events-using-wrl.md)<br/>
Pokazuje, jak używać biblioteki szablonów C++ środowisko wykonawcze systemu Windows, aby subskrybować i obsłużyć zdarzenia obiektu środowisko wykonawcze systemu Windows.

[Przewodnik: tworzenie aplikacji platformy uniwersalnej systemu Windows z użyciem biblioteki WRL i platformy Media Foundation](walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation.md)<br/>
Dowiedz się, jak utworzyć aplikację platformy UWP, która używa [Microsoft Media Foundation](/windows/win32/medfound/microsoft-media-foundation-sdk).

[Instrukcje: Tworzenie klasycznego składnika COM](how-to-create-a-classic-com-component-using-wrl.md)<br/>
Pokazuje, jak używać biblioteki szablonów C++ środowisko wykonawcze systemu Windows do tworzenia podstawowego składnika modelu COM i podstawowego sposobu rejestrowania i używania składnika com z poziomu aplikacji klasycznej.

[Instrukcje: bezpośrednie tworzenie wystąpień składników biblioteki WRL](how-to-instantiate-wrl-components-directly.md)<br/>
Dowiedz się, jak używać funkcji [Microsoft:: WRL:: Make](make-function.md) i [Microsoft:: WRL::D etails:: MakeAndInitialize](makeandinitialize-function.md) , aby utworzyć wystąpienie składnika z modułu, który go definiuje.

[Instrukcje: użycie winmdidl.exe i midlrt.exe w celu utworzenia plików .h z metadanych systemu Windows](use-winmdidl-and-midlrt-to-create-h-files-from-windows-metadata.md)<br/>
Pokazuje, jak używać niestandardowych składników środowisko wykonawcze systemu Windows z WRL przez utworzenie pliku IDL z metadanych. winmd.

[Przewodnik: łączenie za pomocą zadań i żądań XML HTTP](../../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md)<br/>
Pokazuje, w jaki sposób używać interfejsów [IXMLHTTPRequest2](/windows/win32/api/msxml6/nn-msxml6-ixmlhttprequest2) i [IXMLHTTPRequest2Callback](/windows/win32/api/msxml6/nn-msxml6-ixmlhttprequest2callback) wraz z zadaniami do wysyłania żądań HTTP GET i post do usługi sieci Web w aplikacji platformy UWP.

[Przykład Optymalizatora podróży w usłudze mapy Bing](https://code.msdn.microsoft.com/Bing-Maps-trip-optimizer-c4e037f7)<br/>
Używa klasy, która jest zdefiniowana w [instruktażu: `HttpRequest` Łączenie przy użyciu zadań i żądań](../../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md) http XML w kontekście kompletnej aplikacji platformy UWP.

[Tworzenie składnika środowisko wykonawcze systemu Windows DLL z C++ przykładem](https://code.msdn.microsoft.com/windowsapps/Creating-a-Windows-Runtime-6c399797)<br/>
Pokazuje, jak używać biblioteki szablonów C++ środowisko wykonawcze systemu Windows do tworzenia składnika biblioteki DLL w toku i używania go z C++/CX, JavaScript i. C#

[Przykładowa gra DirectX marmur labiryntu](https://code.msdn.microsoft.com/windowsapps/DirectX-Marble-Maze-Game-e4806345)<br/>
Pokazuje, jak używać biblioteki szablonów C++ środowisko wykonawcze systemu Windows do zarządzania okresem istnienia składników modelu COM, takich jak DirectX i Platforma Media Foundation w kontekście kompletnej gry trójwymiarowej.

[Przykład wysyłania wyskakujących powiadomień z aplikacji klasycznych](https://code.msdn.microsoft.com/windowsdesktop/Sending-toast-notifications-71e230a2)<br/>
Pokazuje, jak używać biblioteki szablonów C++ środowisko wykonawcze systemu Windows do pracy z wyskakującymi powiadomieniami z aplikacji klasycznej.

## <a name="windows-runtime-c-template-library-compared-to-atl"></a>Biblioteka C++ szablonów środowisko wykonawcze systemu Windows w porównaniu do ATL

Biblioteka C++ szablonów środowisko wykonawcze systemu Windows jest podobna do Active Template Library (ATL), ponieważ można jej użyć do tworzenia małych i szybkich obiektów com. Biblioteka C++ szablonów środowisko wykonawcze systemu Windows i ATL również współdzielą koncepcje, takie jak definicja obiektów w modułach, jawna Rejestracja interfejsów i otwieranie obiektów przy użyciu fabryk. Znajomość biblioteki szablonów środowisko wykonawcze systemu Windows C++ może być wygodna.

Biblioteka C++ szablonów środowisko wykonawcze systemu Windows obsługuje funkcje com wymagane przez aplikacje platformy UWP. W związku z tym różni się od ATL, ponieważ pomija bezpośrednią obsługę funkcji COM, takich jak:

- agregacji

- implementacje giełdowe

- podwójne interfejsy (`IDispatch`)

- standardowe interfejsy modułu wyliczającego

- punkty połączenia

- interfejsy odrywające

- Osadzanie OLE

- ActiveX — formanty

- COM+

## <a name="concepts"></a>Pojęcia

Biblioteka C++ szablonów środowisko wykonawcze systemu Windows zawiera typy, które reprezentują kilka podstawowych pojęć. W poniższych sekcjach opisano te typy.

### <a name="comptr"></a>ComPtr

[ComPtr](comptr-class.md) to *inteligentny typ wskaźnika* , który reprezentuje interfejs, który jest określony przez parametr szablonu. Użyj `ComPtr` , aby zadeklarować zmienną, która może uzyskać dostęp do elementów członkowskich obiektu, który pochodzi z interfejsu. `ComPtr`automatycznie utrzymuje liczbę odwołań dla wskaźnika źródłowego i zwalnia interfejs, gdy liczba odwołań spadnie do zera.

### <a name="runtimeclass"></a>RuntimeClass

[RuntimeClass](runtimeclass-class.md) reprezentuje klasę skonkretyzowany, która dziedziczy zestaw określonych interfejsów. `RuntimeClass` Obiekt może zapewnić kombinację obsługi jednego lub wielu środowisko wykonawcze systemu Windows interfejsów com lub słabe odwołanie do składnika.

### <a name="module"></a>Moduł

[Moduł](module-class.md) reprezentuje kolekcję obiektów pokrewnych. `Module` Obiekt zarządza fabrykami klas, które tworzą obiekty i rejestrację, co umożliwia innym aplikacjom korzystanie z obiektu.

### <a name="callback"></a>Wywołania zwrotnego

Funkcja [wywołania zwrotnego](callback-function-wrl.md) tworzy obiekt, którego funkcja członkowska jest procedurą obsługi zdarzeń (metoda wywołania zwrotnego). `Callback` Użyj funkcji do zapisywania operacji asynchronicznych.

### <a name="eventsource"></a>EventSource

Element [EventSource](eventsource-class.md) służy do zarządzania obsługą zdarzeń *delegatów* . Użyj środowisko wykonawcze systemu Windows C++ biblioteki szablonów, aby zaimplementować delegata, i `EventSource` użyć do dodawania, usuwania i wywoływania delegatów.

### <a name="asyncbase"></a>AsyncBase

[AsyncBase](asyncbase-class.md) udostępnia metody wirtualne, które reprezentują model programowania asynchronicznego środowisko wykonawcze systemu Windows. Przesłoń składowe w tej klasie, aby utworzyć klasę niestandardową, która może uruchamiać, zatrzymywać lub sprawdzać postęp operacji asynchronicznej.

### <a name="ftmbase"></a>FtmBase

[FtmBase](ftmbase-class.md) reprezentuje obiekt marshaler o dowolnym wątku. `FtmBase`tworzy globalną tabelę interfejsów (GIT) i pomaga zarządzać kierowaniem obiektów i obiektami proxy.

### <a name="weakref"></a>WeakRef

[WeakRef](weakref-class.md) jest typem wskaźnika inteligentnego, który reprezentuje *słabe odwołanie*, które odwołuje się do obiektu, który może lub być niedostępny. `WeakRef` Obiekt może być używany tylko przez środowisko wykonawcze systemu Windows, a nie za pomocą klasycznego modelu com.

`WeakRef` Obiekt zazwyczaj reprezentuje obiekt, którego istnienie jest kontrolowane przez zewnętrzny wątek lub aplikację. Na przykład `WeakRef` obiekt może odwoływać się do obiektu pliku. Gdy plik jest otwarty, `WeakRef` jest prawidłowy i dostępny jest plik, do którego się odwołuje. Ale gdy plik jest zamknięty, `WeakRef` jest nieprawidłowy, a plik jest niedostępny.

## <a name="related-topics"></a>Tematy pokrewne

|||
|-|-|
|[Najważniejsze interfejsy API według kategorii](key-wrl-apis-by-category.md)|Wyróżnia podstawowe typy, C++ funkcje i makra szablonu Środowisko wykonawcze systemu Windows.|
|[Dokumentacja](wrl-reference.md)|Zawiera informacje referencyjne dla biblioteki C++ szablonów środowisko wykonawcze systemu Windows.|
|[Krótkie odwołanie C++/CX)](../../cppcx/quick-reference-c-cx.md)|Zwięźle opisuje funkcje C++/CX, które obsługują środowisko wykonawcze systemu Windows.|
|[Używanie składników środowisko wykonawcze systemu Windows w wizualizacjiC++](/windows/uwp/winrt-components/walkthrough-creating-a-basic-windows-runtime-component-in-cpp-and-calling-it-from-javascript-or-csharp)|Pokazuje, w jaki C++sposób używać/CX do tworzenia podstawowego składnika Środowisko wykonawcze systemu Windows.|
