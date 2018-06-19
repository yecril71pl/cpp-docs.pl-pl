---
title: 'Wskazówki: Łączenie za pomocą zadań i żądań XML HTTP | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- connecting to web services, UWP apps [C++]
- IXMLHTTPRequest2 and tasks, example
- IXHR2 and tasks, example
ms.assetid: e8e12d46-604c-42a7-abfd-b1d1bb2ed6b3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 411d52201aad69a94267615cd0a2acbe6376f64d
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33692590"
---
# <a name="walkthrough-connecting-using-tasks-and-xml-http-requests"></a>Wskazówki: Łączenie za pomocą zadań i żądań XML HTTP
Ten przykład przedstawia sposób użycia [IXMLHTTPRequest2](http://msdn.microsoft.com/en-us/bbc11c4a-aecf-4d6d-8275-3e852e309908) i [IXMLHTTPRequest2Callback](http://msdn.microsoft.com/en-us/aa4b3f4c-6e28-458b-be25-6cce8865fc71) interfejsy wraz z zadań do wysyłania żądań HTTP GET i POST do usługi sieci web w Universal Windows Platform (platformy uniwersalnej systemu Windows ) aplikacji. Połączenie interfejsu `IXMLHTTPRequest2` z zadaniami pozwala pisać kod, który komponuje się z innymi zadaniami. Na przykład zadanie pobierania można umieścić w łańcuchu zadań. Zadanie pobierania może być również inicjowane w odpowiedzi na anulowanie pracy.  
  
> [!TIP]
>  C++ REST SDK służy również do wykonywania żądań HTTP z aplikacji platformy uniwersalnej systemu Windows przy użyciu aplikacji C++ lub z pulpitu aplikacji C++. Aby uzyskać więcej informacji, zobacz [C++ REST SDK (nazwa kodowa "Casablanca")](https://github.com/Microsoft/cpprestsdk).  
  
 Aby uzyskać więcej informacji o zadaniach, zobacz [równoległość zadań](../../parallel/concrt/task-parallelism-concurrency-runtime.md). Aby uzyskać więcej informacji o sposobie używania zadania w aplikacji platformy uniwersalnej systemu Windows, zobacz [asynchronicznego programowania w języku C++](/windows/uwp/threading-async/asynchronous-programming-in-cpp-universal-windows-platform-apps) i [tworzenie operacji asynchronicznych w języku C++ dla aplikacji platformy UWP](../../parallel/concrt/creating-asynchronous-operations-in-cpp-for-windows-store-apps.md).  
  
 W tym dokumencie najpierw pokazano, jak utworzyć klasę `HttpRequest` i jej klasy pomocnicze. Następnie pokaże sposobu korzystania z tej klasy z aplikacji platformy uniwersalnej systemu Windows, który używa C++ i XAML.  
  
 Na przykład bardziej szczegółowy, która używa `HttpReader` klasy opisanych w tym dokumencie, zobacz [tworzenie Bing Maps podróży optymalizatora aplikacji ze Sklepu Windows w JavaScript i C++](http://msdn.microsoft.com/library/974cf025-de1a-4299-b7dd-c6c7bf0e5d30). Innym przykładem, który używa `IXMLHTTPRequest2` , ale nie korzystać z zadań, zobacz [Szybki Start: łączenie za pomocą XML (IXMLHTTPRequest2) żądania HTTP](http://msdn.microsoft.com/en-us/cc7aed53-b2c5-4d83-b85d-cff2f5ba7b35).  
  
> [!TIP]
>  `IXMLHTTPRequest2` i `IXMLHTTPRequest2Callback` interfejsów, które są zalecane do użycia w aplikacji platformy uniwersalnej systemu Windows. Niniejszy przykład można również przystosować do aplikacji klasycznej.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
  
## <a name="defining-the-httprequest-httprequestbufferscallback-and-httprequeststringcallback-classes"></a>Definiowanie klas HttpRequest, HttpRequestBuffersCallback i HttpRequestStringCallback  
 Gdy interfejs `IXMLHTTPRequest2` jest używany do tworzenia żądań sieci Web wysyłanych przez protokół HTTP, następuje zaimplementowanie interfejsu `IXMLHTTPRequest2Callback` w celu odbierania odpowiedzi z serwera i reagowania na inne zdarzenia. W tym przykładzie jest definiowana klasa `HttpRequest` służąca do tworzenia żądań sieci Web oraz klasy `HttpRequestBuffersCallback` i `HttpRequestStringCallback` służące do przetwarzania odpowiedzi. Klasy `HttpRequestBuffersCallback` i `HttpRequestStringCallback` wspierają klasę `HttpRequest`. Użytkownik w kodzie aplikacji pracuje tylko na klasie `HttpRequest`.  
  
 Metody `GetAsync` i `PostAsync` klasy `HttpRequest` umożliwiają inicjowanie operacji HTTP odpowiednio GET i POST. Metody te za pomocą klasy `HttpRequestStringCallback` odczytują odpowiedź serwera jako ciąg tekstowy. Metody `SendAsync` i `ReadAsync` umożliwiają strumieniowe przesyłanie dużej ilości treści we fragmentach. Te metody każdego zwracają [concurrency::task](../../parallel/concrt/reference/task-class.md) reprezentująca operację. Metody `GetAsync` i `PostAsync` generują wartość `task<std::wstring>`, podczas gdy część `wstring` reprezentuje odpowiedź serwera. Metody `SendAsync` i `ReadAsync` generują wartości `task<void>`. Zadania kończą się z chwilą zakończenia operacji wysyłania i odczytu.  
  
 Ponieważ `IXMLHTTPRequest2` interfejsy asynchronicznie działania, w tym przykładzie użyto [concurrency::task_completion_event](../../parallel/concrt/reference/task-completion-event-class.md) Tworzenie zadania kończonego po zakończeniu lub anuluje operację pobierania obiektu wywołania zwrotnego. Klasa `HttpRequest` tworzy na podstawie tego zadania kontynuację opartą na zadaniach, aby wygenerować ostateczny rezultat. Klasa `HttpRequest` wykorzystuje kontynuację opartą na zadaniach do zapewnienia, że kolejne zadania będą wykonywane nawet w przypadku błędu lub anulowania poprzednich zadań. Aby uzyskać więcej informacji na temat kontynuacje opartego na zadaniach, zobacz [równoległość zadania](../../parallel/concrt/task-parallelism-concurrency-runtime.md)  
  
 Aby zapewnić obsługę anulowania, klasy `HttpRequest`, `HttpRequestBuffersCallback` i `HttpRequestStringCallback` używają tokenów anulowania. `HttpRequestBuffersCallback` i `HttpRequestStringCallback` klasy użyj [concurrency::cancellation_token::register_callback](reference/cancellation-token-class.md#register_callback) metodę umożliwiającą włączenie zdarzenie ukończenia zadania odpowiada do anulowania. To zwrotne wywołanie anulowania przerywa operację pobierania. Aby uzyskać więcej informacji na temat anulowania, zobacz [anulowania](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md#cancellation).  
  
#### <a name="to-define-the-httprequest-class"></a>Aby zdefiniować klasę HttpRequest  
  
1.  Użyj Visual C++ **pusta aplikacja (XAML)** szablonu, aby utworzyć pusty projekt aplikacji XAML. W tym przykładzie nazwy projektu `UsingIXMLHTTPRequest2`.  
  
2.  Dodaj do projektu plik nagłówkowy o nazwie HttpRequest.h oraz plik źródłowy o nazwie HttpRequest.cpp.  
  
3.  W pliku pch.h dodaj następujący kod:  
  
     [!code-cpp[concrt-using-ixhr2#1](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_1.h)]  
  
4.  W pliku HttpRequest.h dodaj następujący kod:  
  
     [!code-cpp[concrt-using-ixhr2#2](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_2.h)]  
  
5.  W pliku HttpRequest.cpp dodaj następujący kod:  
  
     [!code-cpp[concrt-using-ixhr2#3](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_3.cpp)]  
  
## <a name="using-the-httprequest-class-in-a-uwp-app"></a>Za pomocą klasy HttpRequest w aplikacji platformy uniwersalnej systemu Windows  
 W tej sekcji przedstawiono sposób użycia `HttpRequest` klasy w aplikacji platformy uniwersalnej systemu Windows. Aplikacja zawiera pole wprowadzania danych definiujące zasób adresu URL, polecenia przycisków wykonujące operacje GET i POST oraz polecenie przycisku, które anuluje bieżącą operację.  
  
#### <a name="to-use-the-httprequest-class"></a>Aby użyć klasy HttpRequest  
  
1.  W MainPage.xaml, zdefiniuj [Panel stosu](http://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.stackpanel.aspx) elementu w następujący sposób.  
  
     [!code-xml[concrt-using-ixhr2#A1](../../parallel/concrt/codesnippet/xaml/walkthrough-connecting-using-tasks-and-xml-http-requests_4.xaml)]  
  
2.  W pliku MainPage.xaml.h dodaj następującą dyrektywę `#include`:  
  
     [!code-cpp[concrt-using-ixhr2#A2](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_5.h)]  
  
3.  W pliku MainPage.xaml.h dodaj następujące zmienne składowe `private` do klasy `MainPage`:  
  
     [!code-cpp[concrt-using-ixhr2#A3](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_6.h)]  
  
4.  W pliku MainPage.xaml.h zadeklaruj metodę `private``ProcessHttpRequest`:  
  
     [!code-cpp[concrt-using-ixhr2#A4](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_7.h)]  
  
5.  W pliku MainPage.xaml.cpp dodaj następujące instrukcje `using`:  
  
     [!code-cpp[concrt-using-ixhr2#A5](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_8.cpp)]  
  
6.  W pliku MainPage.xaml.cpp zaimplementuj metody `GetButton_Click`, `PostButton_Click` i `CancelButton_Click` klasy `MainPage`.  
  
     [!code-cpp[concrt-using-ixhr2#A6](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_9.cpp)]  
  
    > [!TIP]


    >  Jeśli aplikacja nie wymaga obsługi anulowania, Przekaż [concurrency::cancellation_token:: Brak](reference/cancellation-token-class.md#none) do `HttpRequest::GetAsync` i `HttpRequest::PostAsync` metody.  


  
7.  W pliku MainPage.xaml.cpp zaimplementuj metodę `MainPage::ProcessHttpRequest`.  
  
     [!code-cpp[concrt-using-ixhr2#A7](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_10.cpp)]  
  
8.  We właściwościach projektu w obszarze **konsolidatora**, **dane wejściowe**, określ `shcore.lib` i `msxml6.lib`.  
  
 Oto działająca aplikacja:  
  
 ![Uruchomionej aplikacji środowiska wykonawczego systemu Windows](../../parallel/concrt/media/concrt_usingixhr2.png "concrt_usingixhr2")  
  
## <a name="next-steps"></a>Następne kroki  
 [Środowisko uruchomieniowe współbieżności — wskazówki](../../parallel/concrt/concurrency-runtime-walkthroughs.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Równoległość zadania](../../parallel/concrt/task-parallelism-concurrency-runtime.md)   
 [Anulowanie w PPL](cancellation-in-the-ppl.md)   
 [Programowanie asynchroniczne w języku C++](/windows/uwp/threading-async/asynchronous-programming-in-cpp-universal-windows-platform-apps)   
 [Tworzenie operacji asynchronicznych w języku C++ dla aplikacji platformy uniwersalnej systemu Windows](../../parallel/concrt/creating-asynchronous-operations-in-cpp-for-windows-store-apps.md)   
 [Szybki Start: Łączenie się za pomocą XML (IXMLHTTPRequest2) żądania HTTP](http://msdn.microsoft.com/en-us/cc7aed53-b2c5-4d83-b85d-cff2f5ba7b35)   
 [Task — klasa (współbieżność środowiska wykonawczego)](../../parallel/concrt/reference/task-class.md)   
 [task_completion_event, klasa](../../parallel/concrt/reference/task-completion-event-class.md)
