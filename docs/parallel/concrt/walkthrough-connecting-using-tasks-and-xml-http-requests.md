---
title: 'Wskazówki: Łączenie za pomocą zadań i żądań XML HTTP'
ms.date: 04/25/2019
helpviewer_keywords:
- connecting to web services, UWP apps [C++]
- IXMLHTTPRequest2 and tasks, example
- IXHR2 and tasks, example
ms.assetid: e8e12d46-604c-42a7-abfd-b1d1bb2ed6b3
ms.openlocfilehash: 2c627a543ec18702bf5358ff0170bec177fd7497
ms.sourcegitcommit: 89d9e1cb08fa872483d1cde98bc2a7c870e505e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "82032268"
---
# <a name="walkthrough-connecting-using-tasks-and-xml-http-requests"></a>Wskazówki: Łączenie za pomocą zadań i żądań XML HTTP

W tym przykładzie pokazano, jak używać interfejsów [IXMLHTTPRequest2](/windows/win32/api/msxml6/nn-msxml6-ixmlhttprequest2) i [IXMLHTTPRequest2Callback](/windows/win32/api/msxml6/nn-msxml6-ixmlhttprequest2callback) wraz z zadaniami do wysyłania żądań HTTP GET i POST do usługi sieci Web w aplikacji platformy uniwersalnej systemu Windows (UWP). Połączenie interfejsu `IXMLHTTPRequest2` z zadaniami pozwala pisać kod, który komponuje się z innymi zadaniami. Na przykład zadanie pobierania można umieścić w łańcuchu zadań. Zadanie pobierania może być również inicjowane w odpowiedzi na anulowanie pracy.

> [!TIP]
> Można również użyć SDK REST języka C++ do wykonywania żądań HTTP z aplikacji platformy uniwersalnej systemu Windows przy użyciu aplikacji C++ lub z klasycznej aplikacji C++. Aby uzyskać więcej informacji, zobacz [C++ REST SDK (nazwa kodowa "Casablanca")](https://github.com/Microsoft/cpprestsdk).

Aby uzyskać więcej informacji o zadaniach, zobacz [Równoległość zadań](../../parallel/concrt/task-parallelism-concurrency-runtime.md). Aby uzyskać więcej informacji na temat używania zadań w aplikacji platformy uniwersalnej systemu Windows, zobacz [Programowanie asynchroniczne w języku C++](/windows/uwp/threading-async/asynchronous-programming-in-cpp-universal-windows-platform-apps) i [Tworzenie operacji asynchronicznych w języku C++ dla aplikacji platformy uniwersalnej](../../parallel/concrt/creating-asynchronous-operations-in-cpp-for-windows-store-apps.md)systemu Windows.

W tym dokumencie najpierw pokazano, jak utworzyć klasę `HttpRequest` i jej klasy pomocnicze. Następnie pokazuje, jak używać tej klasy z aplikacji platformy uniwersalnej systemu i platformy uniwersalnej systemu, która używa języka C++ i XAML.

Aby zapoznać się `IXMLHTTPRequest2` z przykładem, który używa zadań, ale nie używa, zobacz [Szybki start: Łączenie przy użyciu żądania HTTP XML (IXMLHTTPRequest2)](/previous-versions/windows/apps/hh770550\(v=win.10\)).

> [!TIP]
> `IXMLHTTPRequest2`i `IXMLHTTPRequest2Callback` są interfejsy, które zaleca się do użycia w aplikacji platformy uniwersalnej systemu i platformy uniwersalnej systemu. Niniejszy przykład można również przystosować do aplikacji klasycznej.

## <a name="prerequisites"></a>Wymagania wstępne

Obsługa platformy uniwersalnej systemu wizowego jest opcjonalna w programie Visual Studio 2017 i nowszych. Aby go zainstalować, otwórz Instalator programu Visual Studio z menu Start systemu Windows i wybierz wersję używanego programu Visual Studio. Kliknij przycisk **Modyfikuj** i upewnij się, że kafelek **rozwoju platformy uniwersalnej** systemu jest zaznaczony. W obszarze **Składniki opcjonalne** upewnij się, że narzędzia platformy uniwersalnej systemu Windows języka **C++** są sprawdzane. Użyj wersji 141 dla programu Visual Studio 2017 lub wersji 142 dla programu Visual Studio 2019.

## <a name="defining-the-httprequest-httprequestbufferscallback-and-httprequeststringcallback-classes"></a>Definiowanie klas HttpRequest, HttpRequestBuffersCallback i HttpRequestStringCallback

Gdy interfejs `IXMLHTTPRequest2` jest używany do tworzenia żądań sieci Web wysyłanych przez protokół HTTP, następuje zaimplementowanie interfejsu `IXMLHTTPRequest2Callback` w celu odbierania odpowiedzi z serwera i reagowania na inne zdarzenia. W tym przykładzie jest definiowana klasa `HttpRequest` służąca do tworzenia żądań sieci Web oraz klasy `HttpRequestBuffersCallback` i `HttpRequestStringCallback` służące do przetwarzania odpowiedzi. Klasy `HttpRequestBuffersCallback` i `HttpRequestStringCallback` wspierają klasę `HttpRequest`. Użytkownik w kodzie aplikacji pracuje tylko na klasie `HttpRequest`.

Metody `GetAsync` i `PostAsync` klasy `HttpRequest` umożliwiają inicjowanie operacji HTTP odpowiednio GET i POST. Metody te za pomocą klasy `HttpRequestStringCallback` odczytują odpowiedź serwera jako ciąg tekstowy. Metody `SendAsync` i `ReadAsync` umożliwiają strumieniowe przesyłanie dużej ilości treści we fragmentach. Te metody każdego zwraca [współbieżności::task](../../parallel/concrt/reference/task-class.md) do reprezentowania operacji. Metody `GetAsync` i `PostAsync` generują wartość `task<std::wstring>`, podczas gdy część `wstring` reprezentuje odpowiedź serwera. Metody `SendAsync` i `ReadAsync` generują wartości `task<void>`. Zadania kończą się z chwilą zakończenia operacji wysyłania i odczytu.

Ponieważ `IXMLHTTPRequest2` interfejsy działają asynchronicznie, w tym przykładzie używa [współbieżności::task_completion_event](../../parallel/concrt/reference/task-completion-event-class.md) do utworzenia zadania, które kończy się po zakończeniu obiektu wywołania zwrotnego lub anuluje operację pobierania. Klasa `HttpRequest` tworzy na podstawie tego zadania kontynuację opartą na zadaniach, aby wygenerować ostateczny rezultat. Klasa `HttpRequest` wykorzystuje kontynuację opartą na zadaniach do zapewnienia, że kolejne zadania będą wykonywane nawet w przypadku błędu lub anulowania poprzednich zadań. Aby uzyskać więcej informacji na temat kontynuacji opartych na zadaniach, zobacz [Równoległość zadań](../../parallel/concrt/task-parallelism-concurrency-runtime.md)

Aby zapewnić obsługę anulowania, klasy `HttpRequest`, `HttpRequestBuffersCallback` i `HttpRequestStringCallback` używają tokenów anulowania. Klasy `HttpRequestBuffersCallback` `HttpRequestStringCallback` i używają [metody współbieżności::cancellation_token::register_callback,](reference/cancellation-token-class.md#register_callback) aby umożliwić zdarzenie ukończenia zadania w odpowiedzi na anulowanie. To zwrotne wywołanie anulowania przerywa operację pobierania. Aby uzyskać więcej informacji na temat anulowania, zobacz [Anulowanie](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md#cancellation).

### <a name="to-define-the-httprequest-class"></a>Aby zdefiniować klasę HttpRequest

1. Z menu głównego wybierz polecenie **Plik** > **nowego** > **projektu**.

1. Użyj szablonu Pusta aplikacja języka C++ **(Uniwersalny system Windows),** aby utworzyć pusty projekt aplikacji XAML. W tym przykładzie nazwa projektu `UsingIXMLHTTPRequest2`.

1. Dodaj do projektu plik nagłówkowy o nazwie HttpRequest.h oraz plik źródłowy o nazwie HttpRequest.cpp.

1. W pliku pch.h dodaj następujący kod:

   [!code-cpp[concrt-using-ixhr2#1](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_1.h)]

1. W pliku HttpRequest.h dodaj następujący kod:

   [!code-cpp[concrt-using-ixhr2#2](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_2.h)]

1. W pliku HttpRequest.cpp dodaj następujący kod:

   [!code-cpp[concrt-using-ixhr2#3](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_3.cpp)]

## <a name="using-the-httprequest-class-in-a-uwp-app"></a>Korzystanie z klasy HttpRequest w aplikacji platformy uniwersalnej systemu ws.

W tej sekcji pokazano, `HttpRequest` jak używać klasy w aplikacji platformy uniwersalnej systemu i odpowiedzi. Aplikacja zawiera pole wprowadzania danych definiujące zasób adresu URL, polecenia przycisków wykonujące operacje GET i POST oraz polecenie przycisku, które anuluje bieżącą operację.

### <a name="to-use-the-httprequest-class"></a>Aby użyć klasy HttpRequest

1. W mainpage.xaml zdefiniuj [element StackPanel](/uwp/api/windows.ui.xaml.controls.stackpanel) w następujący sposób.

   [!code-xml[concrt-using-ixhr2#A1](../../parallel/concrt/codesnippet/xaml/walkthrough-connecting-using-tasks-and-xml-http-requests_4.xaml)]

1. W pliku MainPage.xaml.h dodaj następującą dyrektywę `#include`:

   [!code-cpp[concrt-using-ixhr2#A2](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_5.h)]

1. W pliku MainPage.xaml.h dodaj następujące zmienne składowe `private` do klasy `MainPage`:

   [!code-cpp[concrt-using-ixhr2#A3](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_6.h)]

1. W pliku MainPage.xaml.h zadeklaruj metodę `private``ProcessHttpRequest`:

   [!code-cpp[concrt-using-ixhr2#A4](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_7.h)]

1. W pliku MainPage.xaml.cpp dodaj następujące instrukcje `using`:

   [!code-cpp[concrt-using-ixhr2#A5](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_8.cpp)]

1. W pliku MainPage.xaml.cpp zaimplementuj metody `GetButton_Click`, `PostButton_Click` i `CancelButton_Click` klasy `MainPage`.

   [!code-cpp[concrt-using-ixhr2#A6](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_9.cpp)]

   > [!TIP]
   > Jeśli aplikacja nie wymaga obsługi anulowania, przekaż [współbieżność::cancellation_token::none](reference/cancellation-token-class.md#none) do `HttpRequest::GetAsync` i `HttpRequest::PostAsync` metod.

1. W pliku MainPage.xaml.cpp zaimplementuj metodę `MainPage::ProcessHttpRequest`.

   [!code-cpp[concrt-using-ixhr2#A7](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_10.cpp)]

1. We właściwościach projektu w obszarze **Konsolidator**, **Input**określ `shcore.lib` i `msxml6.lib`.

Oto działająca aplikacja:

![Uruchomiona aplikacja środowiska wykonawczego systemu Windows](../../parallel/concrt/media/concrt_usingixhr2.png "Uruchomiona aplikacja środowiska wykonawczego systemu Windows")

## <a name="next-steps"></a>Następne kroki

[Wskazówki dotyczące środowiska uruchomieniowego współbieżności](../../parallel/concrt/concurrency-runtime-walkthroughs.md)

## <a name="see-also"></a>Zobacz też

[Równoległość zadań](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br/>
[Anulowanie w PPL](cancellation-in-the-ppl.md)<br/>
[Programowanie asynchroniczne w języku C++](/windows/uwp/threading-async/asynchronous-programming-in-cpp-universal-windows-platform-apps)<br/>
[Tworzenie operacji asynchronicznych w języku C++ dla aplikacji platformy uniwersalnej systemu Windows](../../parallel/concrt/creating-asynchronous-operations-in-cpp-for-windows-store-apps.md)<br/>
[Szybki start: łączenie się przy użyciu klasy zadania żądania HTTP XML (IXMLHTTPRequest2)](/previous-versions/windows/apps/hh770550\(v=win.10\))
[(środowisko uruchomieniowe współbieżności)](../../parallel/concrt/reference/task-class.md)<br/>
[Klasa task_completion_event](../../parallel/concrt/reference/task-completion-event-class.md)
