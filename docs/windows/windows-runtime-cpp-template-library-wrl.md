---
title: Biblioteka szablonów języka C++ środowiska wykonawczego systemu Windows (WRL)
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: b915afce-553b-44a7-b8dc-0ab601758eb0
ms.openlocfilehash: 484718ee044b752c381d54b471a33e58ca470d80
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/10/2018
ms.locfileid: "51520663"
---
# <a name="windows-runtime-c-template-library-wrl"></a>Biblioteka szablonów języka C++ środowiska wykonawczego systemu Windows (WRL)

Zestaw Windows środowiska uruchomieniowego C++ szablon biblioteki (WRL) to Biblioteka szablonów, która zapewnia niskopoziomowy sposób tworzenia i używania składników środowiska wykonawczego Windows.

> [!NOTE]
> WRL teraz zostało zastąpione przez C + +/ WinRT, standard C ++ 17 języka rzutowanie dla interfejsów API środowiska wykonawczego Windows. C + +/ WinRT jest dostępna w Windows 10 SDK z wersji 1803 wartości. C + +/ WinRT jest zaimplementowana w całości w plikach nagłówkowych i przeznaczone do zapewnia najwyższej jakości dostęp do nowoczesnego interfejsu Windows API.
>
> Za pomocą C + +/ WinRT, można używać lub Tworzenie interfejsów API środowiska wykonawczego Windows przy użyciu dowolnej zgodnych ze standardami języka C ++ 17 kompilatora. C + +/ WinRT zazwyczaj działa lepiej i generuje mniejsze pliki binarne niż innych opcji języka dla środowiska wykonawczego Windows. Firma Microsoft będzie obsługiwać C + +/ CX i WRL, ale zdecydowanie zalecamy, aby użyć nowych aplikacji C + +/ WinRT. Aby uzyskać więcej informacji, zobacz [C + +/ WinRT](https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/index).

## <a name="benefits"></a>Zalety

Biblioteka szablonów C++ środowiska wykonawczego Windows pozwala łatwiej wdrażać i wykorzystywać składniki Component Object Model (COM). Zapewnia techniki porządkowe, takie jak zliczanie odwołań, aby zarządzać okresem istnienia obiektów i testowanie wartości HRESULT, aby ustalić, czy operacja zakończyła się pomyślnie lub nie powiodło się. Aby pomyślnie korzystać Biblioteka szablonów C++ środowiska wykonawczego Windows, należy dokładnie przestrzegać tych zasad i technik.

C + +/ CX jest wysokiego poziomu, opartych na języku sposób używania składników środowiska wykonawczego Windows. Zarówno Biblioteka szablonów C++ środowiska wykonawczego Windows, jak i C + +/ CX uproszczają pisanie kodu dla środowiska uruchomieniowego Windows przez automatyczne wykonywanie zadań porządkowych w Twoim imieniu.

Biblioteka szablonów C++ środowiska wykonawczego Windows i C + +/ CX oferują różne korzyści. Oto kilka powodów, możesz chcieć użyć Biblioteka szablonów C++ środowiska wykonawczego Windows zamiast C + +/ CX:

- Biblioteka szablonów C++ środowiska wykonawczego Windows dodaje pewien poziom abstrakcji za pośrednictwem Windows Runtime aplikacji binarny interfejsu (ABI), co daje możliwość sterowania podstawowym kodem, aby lepiej tworzyć lub korzystać z interfejsów API środowiska wykonawczego Windows.

- C + +/ CX reprezentuje wartości COM HRESULT jako wyjątki. Jeśli już odziedziczyłeś bazę kodów używających COM lub taką, która nie korzysta z wyjątków, może się okazać, że biblioteka szablonów C++ środowiska wykonawczego Windows jest bardziej naturalny sposób pracy ze środowiskiem uruchomieniowym Windows, ponieważ nie trzeba używać wyjątków.

   > [!NOTE]
   > Biblioteka szablonów C++ środowiska wykonawczego Windows używa wartości HRESULT i nie zgłasza wyjątków. Ponadto Biblioteka szablonów C++ środowiska wykonawczego Windows używa inteligentne wskaźniki i wzór RAII w celu zagwarantowania, że obiekty są poprawnie niszczone, gdy kod aplikacji zgłasza wyjątek. Aby uzyskać więcej informacji dotyczących inteligentnych wskaźników i idiomu RAII, zobacz [inteligentne wskaźniki](../cpp/smart-pointers-modern-cpp.md) i [obiektów własne zasoby (RAII)](../cpp/objects-own-resources-raii.md).

- Cel i Projekt Biblioteka szablonów C++ środowiska wykonawczego Windows są INSPIROWANE przez Active Template Library (ATL), która stanowi zestaw oparty na szablonie klasy C++, które upraszczają programowanie obiektów COM. Biblioteka szablonów C++ środowiska wykonawczego Windows używa standardowego języka C++, aby opakować środowiska wykonawczego Windows, można łatwiej portu i korzystać z wielu istniejących składników COM napisanych w ATL do środowiska wykonawczego Windows. Jeśli już znasz ATL, może się okazać, że programowanie Biblioteka szablonów C++ środowiska wykonawczego Windows jest łatwiejsze.

## <a name="getting-started"></a>Wprowadzenie

Poniżej przedstawiono niektóre zasoby, które mogą pomóc Ci rozpocząć pracę z Biblioteka szablonów C++ środowiska wykonawczego Windows, następnie od razu.

[Biblioteka środowiska uruchomieniowego Windows (WRL)](https://channel9.msdn.com/Events/Windows-Camp/Developing-Windows-8-Metro-style-apps-in-Cpp/The-Windows-Runtime-Library-WRL-)<br/>
W tym filmie wideo Channel 9 Dowiedz się więcej o jak Biblioteka szablonów C++ środowiska wykonawczego Windows ułatwia pisanie aplikacji uniwersalnych platformy Windows (UWP) i jak tworzyć i wykorzystywać składniki środowiska uruchomieniowego Windows.

[Porady: uaktywnianie składnika środowiska wykonawczego Windows i korzystanie](../windows/how-to-activate-and-use-a-windows-runtime-component-using-wrl.md)<br/>
Pokazuje, jak używać Biblioteka szablonów C++ środowiska wykonawczego Windows można zainicjować aparatu plików wykonywalnych Windows oraz uaktywnienia i używania składnika wykonawczego Windows.

[Porady: wykonywanie operacji asynchronicznych](../windows/how-to-complete-asynchronous-operations-using-wrl.md)<br/>
Pokazuje, jak używać Biblioteka szablonów C++ środowiska wykonawczego Windows do uruchamiania operacji asynchronicznych i wykonywania pracy po ukończeniu operacji.

[Porady: Obsługa zdarzeń](../windows/how-to-handle-events-using-wrl.md)<br/>
Pokazuje, jak używać Biblioteka szablonów C++ środowiska wykonawczego Windows subskrybować, i obsługiwać zdarzenia obiektu Windows Runtime.

[Przewodnik: tworzenie aplikacji platformy uniwersalnej systemu Windows z użyciem biblioteki WRL i platformy Media Foundation](../windows/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation.md)<br/>
Dowiedz się, jak utworzyć aplikację platformy uniwersalnej systemu Windows, która używa [Microsoft Media Foundation](/windows/desktop/medfound/microsoft-media-foundation-sdk).

[Porady: tworzenie klasycznego składnika COM](../windows/how-to-create-a-classic-com-component-using-wrl.md)<br/>
Pokazuje, jak używać Biblioteka szablonów C++ środowiska wykonawczego Windows do tworzenia podstawowego składnika modelu COM i podstawowy sposób zarejestrowania i używania składnika COM z aplikacji klasycznej.

[Instrukcje: bezpośrednie tworzenie wystąpień składników biblioteki WRL](../windows/how-to-instantiate-wrl-components-directly.md)<br/>
Dowiedz się, jak używać [Microsoft::wrl:: Make](../windows/make-function.md) i [Microsoft::WRL::Details::MakeAndInitialize](../windows/makeandinitialize-function.md) celu utworzenia instancji składnika z modułu, który go definiuje.

[Instrukcje: Użyj winmdidl.exe i midlrt.exe, aby utworzyć pliki .h z metadanych systemu Windows](../windows/use-winmdidl-and-midlrt-to-create-h-files-from-windows-metadata.md)<br/>
Pokazuje sposób wykorzystywania niestandardowych składników Windows Runtime z WRL przez utworzenie pliku IDL z metadanych .winmd.

[Przewodnik: łączenie za pomocą zadań i żądań XML HTTP](../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md)<br/>
Ilustruje sposób używania [IXMLHTTPRequest2](/windows/desktop/api/msxml6/nn-msxml6-ixmlhttprequest2) i [IXMLHTTPRequest2Callback](/windows/desktop/api/msxml6/nn-msxml6-ixmlhttprequest2callback) interfejsów oraz zadań wysyłać żądania HTTP GET i POST do usługi sieci web w aplikacji platformy uniwersalnej systemu Windows.

[Przykład optymalizatora podróży w mapach Bing](https://code.msdn.microsoft.com/Bing-Maps-trip-optimizer-c4e037f7)<br/>
Używa `HttpRequest` klasy, która jest zdefiniowana w [wskazówki: łączenie za pomocą zadań i żądań XML HTTP](../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md) w kontekście pełnej aplikacji platformy uniwersalnej systemu Windows.

[Tworzenie składnika biblioteki DLL środowiska uruchomieniowego Windows przy użyciu przykładu w języku C++](https://code.msdn.microsoft.com/windowsapps/Creating-a-Windows-Runtime-6c399797)<br/>
Pokazuje, jak Biblioteka szablonów C++ środowiska wykonawczego Windows umożliwiają tworzenie składnika biblioteki DLL w procesie i używanie go z C + +/ CX, JavaScript i C#.

[Przykładowa gra programu DirectX marmurowy Labirynt](https://code.msdn.microsoft.com/windowsapps/DirectX-Marble-Maze-Game-e4806345)<br/>
Pokazuje, jak na potrzeby zarządzania okresem istnienia składników COM, takich jak DirectX i platformy Media Foundation w kontekście Zakończenie gry 3-w. Biblioteka szablonów C++ środowiska wykonawczego Windows.

[Wysyłania powiadomień toast z przykładowej aplikacji klasycznych](https://code.msdn.microsoft.com/windowsdesktop/Sending-toast-notifications-71e230a2)<br/>
Pokazuje, jak używać Biblioteka szablonów C++ środowiska wykonawczego Windows do pracy z powiadomieniami toast z aplikacji klasycznej.

## <a name="windows-runtime-c-template-library-compared-to-atl"></a>Biblioteka szablonów języka C++ środowiska wykonawczego Windows w porównaniu z ATL

Biblioteka szablonów C++ środowiska wykonawczego Windows przypomina Active Template Library (ATL), ponieważ służy do tworzenia małych, szybkich obiektów COM. Biblioteka szablonów C++ środowiska wykonawczego Windows i ATL również współdzielą pojęcia, takie jak definicje obiektów w modułach, jawna rejestracja interfejsów i otwarte Tworzenie obiektów przy użyciu fabryk. Może się komfortowo, jednocześnie Biblioteka szablonów C++ środowiska wykonawczego Windows, jeśli znasz ATL.

Biblioteka szablonów C++ środowiska wykonawczego Windows obsługuje funkcję COM, która jest wymagana dla aplikacji platformy uniwersalnej systemu Windows. W związku z tym różni się od ATL ponieważ pomija bezpośrednią obsługę funkcji COM takich jak:

- Agregacji

- implementacje magazynu

- podwójne interfejsy (`IDispatch`)

- standardowe interfejsy modułu wyliczającego

- punkty połączenia

- interfejsy odrywania

- Osadzanie OLE

- kontrolki ActiveX

- COM+

## <a name="concepts"></a>Pojęcia

Biblioteka szablonów C++ środowiska wykonawczego Windows zawiera typy, które reprezentują kilka podstawowych pojęć. W poniższych sekcjach opisano te typy.

### <a name="comptr"></a>ComPtr

[ComPtr](../windows/comptr-class.md) jest *inteligentny wskaźnik* typ, który reprezentuje interfejs, który jest określony przez parametr szablonu. Użyj `ComPtr` Aby zadeklarować zmienną, która ma dostęp do członków obiektu, który pochodzi z interfejsu. `ComPtr` automatycznie przechowuje licznik odwołań dla podstawowego wskaźnika interfejsu i zwalnia interfejs gdy liczba odwołań osiąga zero.

### <a name="runtimeclass"></a>RuntimeClass

[RuntimeClass](../windows/runtimeclass-class.md) reprezentuje skonkretyzowaną klasę, która dziedziczy zestaw określonych interfejsów. Element `RuntimeClass` obiektu może zapewnić kombinację obsługi dla jednego lub więcej interfejsów COM środowiska uruchomieniowego Windows lub słabe odwołanie do składnika.

### <a name="module"></a>Moduł

[Moduł](../windows/module-class.md) reprezentuje kolekcję obiektów pokrewnych. Element `Module` obiektu zarządza fabrykami klas, które tworzą obiekty i rejestracji, które umożliwiają innym aplikacjom używanie obiektu.

### <a name="callback"></a>Wywołanie zwrotne

[Wywołania zwrotnego](../windows/callback-function-windows-runtime-cpp-template-library.md) funkcja tworzy obiekt, którego funkcja członkowska jest program obsługi zdarzeń (metody wywołania zwrotnego). Użyj `Callback` funkcję, aby pisać operacje asynchroniczne.

### <a name="eventsource"></a>EventSource

[EventSource](../windows/eventsource-class.md) służy do zarządzania *delegować* procedury obsługi zdarzeń. Użyj Biblioteka szablonów C++ środowiska wykonawczego Windows, aby zaimplementować delegata, a następnie użyj `EventSource` można dodawać, usuwać i wywoływać delegatów.

### <a name="asyncbase"></a>AsyncBase

[AsyncBase](../windows/asyncbase-class.md) dostarcza metody wirtualne, które reprezentują model programowania asynchronicznego środowiska wykonawczego Windows. Zastąp członków w tej klasie do tworzenia niestandardowych klas, które uruchomić, zatrzymać lub sprawdzić postęp operacji asynchronicznej.

### <a name="ftmbase"></a>FtmBase

[FtmBase](../windows/ftmbase-class.md) reprezentuje obiekt bezwątkowego. `FtmBase` tworzy tabelę interfejsu globalnego (GIT) i pomaga zarządzać obiektami organizowania i pośredniczących.

### <a name="weakref"></a>WeakRef

[WeakRef](../windows/weakref-class.md) jest typem wskaźnika inteligentnego, który reprezentuje *słabe odwołanie*, które odwołują się do obiektu, który może być lub może być niedostępny. A `WeakRef` obiekt może być używany przez tylko środowiska wykonawczego Windows, a nie przez Klasyczny model COM.

A `WeakRef` zazwyczaj obiekt reprezentuje obiekt, którego istnienie jest kontrolowane przez zewnętrzny wątek lub aplikację. Na przykład `WeakRef` obiektu może odwoływać się do obiektu pliku. Gdy plik jest otwarty, `WeakRef` jest prawidłowy i przywoływany plik jest dostępny. Jednak po zamknięciu pliku `WeakRef` jest nieprawidłowy i pliku nie jest dostępny.

## <a name="related-topics"></a>Tematy pokrewne

|||
|-|-|
|[Kluczowe interfejsy API, według kategorii](../windows/key-wrl-apis-by-category.md)|Podświetla podstawowe typy Biblioteka szablonów C++ środowiska wykonawczego Windows, funkcje i makra.|
|[Dokumentacja](../windows/wrl-reference.md)|Zawiera informacje dotyczące Biblioteka szablonów C++ środowiska wykonawczego Windows.|
|[Krótki przewodnik (środowisko uruchomieniowe Windows i Visual C++)](../cppcx/quick-reference-c-cx.md)|Krótko opisano C + +/ CX funkcji, obsługujące środowiska wykonawczego Windows.|
|[Za pomocą składników środowiska wykonawczego Windows w języku Visual C++](/windows/uwp/winrt-components/walkthrough-creating-a-basic-windows-runtime-component-in-cpp-and-calling-it-from-javascript-or-csharp)|Pokazuje, jak używać języka C + +/ CX do utworzenia podstawowego składnika środowiska wykonawczego Windows.|
