---
title: 'Wskazówki: Łączenie za pomocą zadań i żądań XML HTTP'
ms.date: 04/25/2019
helpviewer_keywords:
- connecting to web services, UWP apps [C++]
- IXMLHTTPRequest2 and tasks, example
- IXHR2 and tasks, example
ms.assetid: e8e12d46-604c-42a7-abfd-b1d1bb2ed6b3
ms.openlocfilehash: cdcdd4747e7f32d1d4c0e91959f4b49a45721269
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224906"
---
# <a name="walkthrough-connecting-using-tasks-and-xml-http-requests"></a>Wskazówki: Łączenie za pomocą zadań i żądań XML HTTP

Ten przykład pokazuje, jak używać interfejsów [IXMLHTTPRequest2](/windows/win32/api/msxml6/nn-msxml6-ixmlhttprequest2) i [IXMLHTTPRequest2Callback](/windows/win32/api/msxml6/nn-msxml6-ixmlhttprequest2callback) wraz z zadaniami do wysyłania żądań HTTP GET i post do usługi sieci Web w aplikacji platforma uniwersalna systemu Windows (platformy UWP). Połączenie interfejsu `IXMLHTTPRequest2` z zadaniami pozwala pisać kod, który komponuje się z innymi zadaniami. Na przykład zadanie pobierania można umieścić w łańcuchu zadań. Zadanie pobierania może być również inicjowane w odpowiedzi na anulowanie pracy.

> [!TIP]
> Możesz również użyć zestawu SDK REST C++ do wykonywania żądań HTTP z aplikacji platformy UWP przy użyciu aplikacji C++ lub aplikacji klasycznej w języku C++. Aby uzyskać więcej informacji, zobacz [C++ REST SDK (nazwa kodowa "Casablanca")](https://github.com/Microsoft/cpprestsdk).

Aby uzyskać więcej informacji o zadaniach, zobacz [równoległość zadań](../../parallel/concrt/task-parallelism-concurrency-runtime.md). Aby uzyskać więcej informacji o sposobach korzystania z zadań w aplikacji platformy UWP, zobacz [programowanie asynchroniczne w języku c++](/windows/uwp/threading-async/asynchronous-programming-in-cpp-universal-windows-platform-apps) i [Tworzenie operacji asynchronicznych w języku C++ dla aplikacji platformy UWP](../../parallel/concrt/creating-asynchronous-operations-in-cpp-for-windows-store-apps.md).

W tym dokumencie najpierw pokazano, jak utworzyć klasę `HttpRequest` i jej klasy pomocnicze. Następnie pokazano, jak używać tej klasy z poziomu aplikacji platformy UWP używającej języków C++ i XAML.

Aby zapoznać się z przykładem, który używa `IXMLHTTPRequest2` , ale nie używa zadań, zobacz [Szybki Start: Nawiązywanie połączenia za pomocą XML żądanie HTTP (IXMLHTTPRequest2)](/previous-versions/windows/apps/hh770550\(v=win.10\)).

> [!TIP]
> `IXMLHTTPRequest2`i `IXMLHTTPRequest2Callback` są interfejsami zalecanymi do użycia w aplikacji platformy UWP. Niniejszy przykład można również przystosować do aplikacji klasycznej.

## <a name="prerequisites"></a>Wymagania wstępne

Obsługa platformy UWP jest opcjonalna w programie Visual Studio 2017 i nowszych. Aby go zainstalować, Otwórz Instalator programu Visual Studio z menu Start systemu Windows i wybierz używaną wersję programu Visual Studio. Kliknij przycisk **Modyfikuj** i upewnij się, że jest zaznaczony kafelek **programowanie platformy UWP** . W obszarze **składniki opcjonalne** upewnij się, że są zaznaczone **Narzędzia C++ platformy UWP Tools** . Użyj najnowsze 141 dla programu Visual Studio 2017 lub v142 dla programu Visual Studio 2019.

## <a name="defining-the-httprequest-httprequestbufferscallback-and-httprequeststringcallback-classes"></a>Definiowanie klas HttpRequest, HttpRequestBuffersCallback i HttpRequestStringCallback

Gdy interfejs `IXMLHTTPRequest2` jest używany do tworzenia żądań sieci Web wysyłanych przez protokół HTTP, następuje zaimplementowanie interfejsu `IXMLHTTPRequest2Callback` w celu odbierania odpowiedzi z serwera i reagowania na inne zdarzenia. W tym przykładzie jest definiowana klasa `HttpRequest` służąca do tworzenia żądań sieci Web oraz klasy `HttpRequestBuffersCallback` i `HttpRequestStringCallback` służące do przetwarzania odpowiedzi. Klasy `HttpRequestBuffersCallback` i `HttpRequestStringCallback` wspierają klasę `HttpRequest`. Użytkownik w kodzie aplikacji pracuje tylko na klasie `HttpRequest`.

Metody `GetAsync` i `PostAsync` klasy `HttpRequest` umożliwiają inicjowanie operacji HTTP odpowiednio GET i POST. Metody te za pomocą klasy `HttpRequestStringCallback` odczytują odpowiedź serwera jako ciąg tekstowy. Metody `SendAsync` i `ReadAsync` umożliwiają strumieniowe przesyłanie dużej ilości treści we fragmentach. Metody te zwracają wartość [concurrency:: Task](../../parallel/concrt/reference/task-class.md) , aby reprezentować operację. Metody `GetAsync` i `PostAsync` generują wartość `task<std::wstring>`, podczas gdy część `wstring` reprezentuje odpowiedź serwera. Metody `SendAsync` i `ReadAsync` generują wartości `task<void>`. Zadania kończą się z chwilą zakończenia operacji wysyłania i odczytu.

Ponieważ `IXMLHTTPRequest2` interfejsy działają asynchronicznie, w tym przykładzie używa [concurrency:: task_completion_event](../../parallel/concrt/reference/task-completion-event-class.md) , aby utworzyć zadanie, które kończy się po zakończeniu obiektu wywołania zwrotnego lub anuluje operację pobierania. Klasa `HttpRequest` tworzy na podstawie tego zadania kontynuację opartą na zadaniach, aby wygenerować ostateczny rezultat. Klasa `HttpRequest` wykorzystuje kontynuację opartą na zadaniach do zapewnienia, że kolejne zadania będą wykonywane nawet w przypadku błędu lub anulowania poprzednich zadań. Aby uzyskać więcej informacji dotyczących kontynuacji opartych na zadaniach, zobacz [równoległość zadań](../../parallel/concrt/task-parallelism-concurrency-runtime.md)

Aby zapewnić obsługę anulowania, klasy `HttpRequest`, `HttpRequestBuffersCallback` i `HttpRequestStringCallback` używają tokenów anulowania. `HttpRequestBuffersCallback`Klasy i `HttpRequestStringCallback` używają metody [concurrency:: cancellation_token:: register_callback](reference/cancellation-token-class.md#register_callback) w celu umożliwienia reakcji na anulowanie zdarzenia ukończenia zadania. To zwrotne wywołanie anulowania przerywa operację pobierania. Aby uzyskać więcej informacji na temat anulowania, zobacz [anulowania](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md#cancellation).

### <a name="to-define-the-httprequest-class"></a>Aby zdefiniować klasę HttpRequest

1. Z menu głównego wybierz pozycję **plik**  >  **Nowy**  >  **projekt**.

1. Użyj szablonu języka C++ **pustej aplikacji (uniwersalnego systemu Windows)** , aby utworzyć pusty projekt aplikacji XAML. Ten przykład nazywa projekt `UsingIXMLHTTPRequest2` .

1. Dodaj do projektu plik nagłówkowy o nazwie HttpRequest.h oraz plik źródłowy o nazwie HttpRequest.cpp.

1. W pliku pch.h dodaj następujący kod:

   [!code-cpp[concrt-using-ixhr2#1](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_1.h)]

1. W pliku HttpRequest.h dodaj następujący kod:

   [!code-cpp[concrt-using-ixhr2#2](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_2.h)]

1. W pliku HttpRequest.cpp dodaj następujący kod:

   [!code-cpp[concrt-using-ixhr2#3](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_3.cpp)]

## <a name="using-the-httprequest-class-in-a-uwp-app"></a>Korzystanie z klasy HttpRequest w aplikacji platformy UWP

W tej sekcji pokazano, jak używać `HttpRequest` klasy w aplikacji platformy UWP. Aplikacja zawiera pole wprowadzania danych definiujące zasób adresu URL, polecenia przycisków wykonujące operacje GET i POST oraz polecenie przycisku, które anuluje bieżącą operację.

### <a name="to-use-the-httprequest-class"></a>Aby użyć klasy HttpRequest

1. W pliku MainPage. XAML Zdefiniuj element [StackPanel](/uwp/api/windows.ui.xaml.controls.stackpanel) w następujący sposób.

   [!code-xml[concrt-using-ixhr2#A1](../../parallel/concrt/codesnippet/xaml/walkthrough-connecting-using-tasks-and-xml-http-requests_4.xaml)]

1. W pliku MainPage.xaml.h dodaj następującą dyrektywę `#include`:

   [!code-cpp[concrt-using-ixhr2#A2](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_5.h)]

1. W MainPage. XAML. h Dodaj te **`private`** zmienne członkowskie do `MainPage` klasy:

   [!code-cpp[concrt-using-ixhr2#A3](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_6.h)]

1. W MainPage. XAML. h Zadeklaruj **`private`** metodę `ProcessHttpRequest` :

   [!code-cpp[concrt-using-ixhr2#A4](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_7.h)]

1. W pliku MainPage. XAML. cpp Dodaj następujące **`using`** instrukcje:

   [!code-cpp[concrt-using-ixhr2#A5](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_8.cpp)]

1. W pliku MainPage.xaml.cpp zaimplementuj metody `GetButton_Click`, `PostButton_Click` i `CancelButton_Click` klasy `MainPage`.

   [!code-cpp[concrt-using-ixhr2#A6](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_9.cpp)]

   > [!TIP]
   > Jeśli aplikacja nie wymaga obsługi anulowania, Przekaż [współbieżność:: cancellation_token:: brak](reference/cancellation-token-class.md#none) do `HttpRequest::GetAsync` `HttpRequest::PostAsync` metod i.

1. W pliku MainPage.xaml.cpp zaimplementuj metodę `MainPage::ProcessHttpRequest`.

   [!code-cpp[concrt-using-ixhr2#A7](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_10.cpp)]

1. We właściwościach projektu w obszarze **konsolidator**, **wejście**, określ `shcore.lib` i `msxml6.lib` .

Oto działająca aplikacja:

![Uruchomiona aplikacja środowisko wykonawcze systemu Windows](../../parallel/concrt/media/concrt_usingixhr2.png "Uruchomiona aplikacja środowisko wykonawcze systemu Windows")

## <a name="next-steps"></a>Następne kroki

[Instruktaże środowisko uruchomieniowe współbieżności](../../parallel/concrt/concurrency-runtime-walkthroughs.md)

## <a name="see-also"></a>Zobacz także

[Równoległość zadań](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br/>
[Anulowanie w PPL](cancellation-in-the-ppl.md)<br/>
[Programowanie asynchroniczne w języku C++](/windows/uwp/threading-async/asynchronous-programming-in-cpp-universal-windows-platform-apps)<br/>
[Tworzenie operacji asynchronicznych w języku C++ dla aplikacji platformy UWP](../../parallel/concrt/creating-asynchronous-operations-in-cpp-for-windows-store-apps.md)<br/>
[Szybki Start: Łączenie przy użyciu żądania HTTP XML (IXMLHTTPRequest2)](/previous-versions/windows/apps/hh770550\(v=win.10\)) 
 [task — Klasa (środowisko uruchomieniowe współbieżności)](../../parallel/concrt/reference/task-class.md)<br/>
[Klasa task_completion_event](../../parallel/concrt/reference/task-completion-event-class.md)
