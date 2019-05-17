---
title: Programowanie chmury i sieci Web w programie Visual C++
ms.date: 05/14/2019
ms.assetid: b63611f1-9723-44d0-ba7f-c3ebef341313
ms.openlocfilehash: 677e9da18e8d171f523994d21bfbd0411270e3c8
ms.sourcegitcommit: bc1b14f29a02685f97c7ef5c098d16db6eaf369f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2019
ms.locfileid: "65790359"
---
# <a name="cloud-and-web-programming-in-visual-c"></a>Programowanie chmury i sieci Web w programie Visual C++

W języku C++ masz kilka opcji do łączenia się z sieci web i w chmurze.

## <a name="microsoft-azure-sdks-and-rest-services"></a>Usługi Microsoft Azure SDK i REST

- [Biblioteki klienta usługi Microsoft Azure Storage dla języka C++](https://azure.github.io/azure-storage-cpp/)

  Biblioteki klienta usługi Azure Storage dla języka C++ zapewnia kompleksowe interfejsu API do pracy z usługą Azure storage, w tym między innymi następujące możliwości:

  - Tworzenie, Odczyt, usuwanie i listy kontenerów obiektów blob, tabel i kolejek.
  - Tworzenie, odczytywanie, usunąć, listy i kopiowania obiektów blob oraz odczytywanie i zapisywanie zakresów obiektów blob.
  - Wstaw, Usuń, Zastąp, scalania i wykonywanie zapytań dotyczących jednostek w tabeli platformy Azure.
  - Umieścić w kolejce i pobierać komunikaty w kolejce platformy Azure.
  - Opóźnieniem listy kontenerów, obiektów blob, tabel i kolejek, a opóźnieniem wykonywać zapytania dla jednostek

- ANSI C99 [zestawami SDK Azure IoT Hub](/azure/iot-hub/iot-hub-devguide-sdks) dla Internetu rzeczy umożliwiają aplikacjom IoT są uruchomione na urządzeniu lub wewnętrznej bazy danych.

- [OneDrive i programem SharePoint w programie Microsoft Graph](https://dev.onedrive.com/README.htm)

  Interfejs API usługi OneDrive zapewnia zestaw usług HTTP do łączenia aplikacji z plików i folderów w usłudze Office 365 i SharePoint Server 2016.

## <a name="windows-and-cross-platform-networking-apis"></a>Windows i sieci dla wielu platform interfejsów API

- [C++REST SDK (nazwa kodowa "Casablanca")](https://github.com/Microsoft/cpprestsdk)

  Udostępnia nowoczesnych dla wielu platform, asynchronicznego interfejsu API do interakcji z usług REST.

  - Wykonania wywołania REST względem dowolnego serwera HTTP z wbudowaną obsługą dokumentów JSON, analizowania i serializacja
  - Obsługuje OAuth 1 i 2, w tym odbiornik przekierowanie lokalnych
  - Nawiązuj kontakty WebSockets względem usługi zdalnej
  - W pełni asynchroniczne zadanie interfejsu API oparte na PPL, łącznie z puli wątków wbudowane

  Obsługuje Windows Desktop (7 i nowsze), Windows Server (2012 i nowsze), Universal Windows Platform, systemu Linux, OSX, Android i iOS.

- [Windows::Web::Http::HttpClient](/uwp/api/windows.web.http.httpclient)

  Klasa klienta HTTP środowiska wykonawczego Windows wzorowana na klasę .NET Framework o tej samej nazwie w przestrzeni nazw System.Web. `HttpClient` w pełni obsługuje asynchroniczne przekazywanie i pobieranie przez HTTP oraz filtry potoku, które umożliwiają wstawianie niestandardowych programów obsługi HTTP do potoku. Zestaw Windows SDK zawiera przykładowe filtry dla mierzonych sieci, uwierzytelnianiem OAuth i inne. W przypadku aplikacji, których platformą docelową tylko Universal Windows Platform, zaleca się używanie `Windows::Web:HttpClient` klasy.

- [Interfejs IXMLHTTPRequest2](/windows/desktop/api/msxml6/nn-msxml6-ixmlhttprequest2)

  Zapewnia macierzysty interfejs COM, że w aplikacji środowiska wykonawczego Windows lub aplikacje pulpitu Windows umożliwiają połączenie z Internetem za pośrednictwem protokołu HTTP i elementu GET, PUT i innych poleceń protokołu HTTP. Aby uzyskać więcej informacji, zobacz [instruktażu: Łączenie za pomocą zadań i żądań XML HTTP](../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md).

- [Windows Internet (WinInet)](/windows/desktop/WinInet/portal)

  Interfejs API Windows, który można użyć w aplikacjach komputerowych Windows, aby nawiązać połączenie z Internetem.

## <a name="see-also"></a>Zobacz także

[Język C++ w programie Visual Studio](../overview/visual-cpp-in-visual-studio.md) <br/>
[Centrum deweloperów języka C++ i C platformy Microsoft Azure](https://azure.microsoft.com/develop/cpp/) <br/>
[Sieci i usług sieci web (systemu Windows UWP)](/windows/uwp/networking/)
