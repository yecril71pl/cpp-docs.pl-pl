---
title: Programowanie chmury i sieci Web w programie Visual C++
ms.date: 11/04/2016
ms.assetid: b63611f1-9723-44d0-ba7f-c3ebef341313
ms.openlocfilehash: 33431a8f8660af683ed2e39e10811c22fe2f4fcc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62385274"
---
# <a name="cloud-and-web-programming-in-visual-c"></a>Programowanie chmury i sieci Web w programie Visual C++

W języku C++ masz kilka opcji do łączenia się z sieci web i w chmurze.

## <a name="cloud-programming-options"></a>Opcje programowania w chmurze

- [Windows Azure Mobile Services](http://www.windowsazure.com/develop/mobile/)

  Zapewnia macierzyste interfejsy API, który można użyć w aplikacji platformy uniwersalnej Windows (UWP) lub aplikacje komputerowe Windows, do łączenia z usługą Windows Azure Mobile Services. Chociaż większość przykładów w witrynie internetowej w języku C#, można również użyć C++. Aby uzyskać więcej informacji, zobacz [Szybki Start: Dodawanie usługi mobilnej w języku C++](https://msdn.microsoft.com/library/windows/apps/dn263181.aspx).

- [Biblioteki klienta usługi Microsoft Azure Storage dla języka C++](https://blogs.msdn.microsoft.com/windowsazurestorage/2015/04/29/microsoft-azure-storage-client-library-for-c-v1-0-0-general-availability/)

  Biblioteki klienta usługi Azure Storage dla języka C++ zapewnia kompleksowe interfejsu API do pracy z usługą Azure storage, w tym między innymi następujące możliwości:

  - Tworzenie, Odczyt, usuwanie i listy kontenerów obiektów blob, tabel i kolejek.
  - Tworzenie, odczytywanie, usunąć, listy i kopiowania obiektów blob oraz odczytywanie i zapisywanie zakresów obiektów blob.
  - Wstaw, Usuń, Zastąp, scalania i wykonywanie zapytań dotyczących jednostek w tabeli platformy Azure.
  - Umieścić w kolejce i pobierać komunikaty w kolejce platformy Azure.
  - Opóźnieniem listy kontenerów, obiektów blob, tabel i kolejek, a opóźnieniem wykonywać zapytania dla jednostek

- [Interfejs API w usłudze OneDrive](https://dev.onedrive.com/README.htm)

  Interfejs API usługi OneDrive zapewnia zestaw usług HTTP do łączenia aplikacji z plików i folderów w usłudze Office 365 i SharePoint Server 2016.

- [C++ REST SDK (nazwa kodowa "Casablanca")](https://github.com/Microsoft/cpprestsdk)

  Udostępnia nowoczesnych dla wielu platform, asynchronicznego interfejsu API do interakcji z usług REST.

  - Wykonania wywołania REST względem dowolnego serwera HTTP z wbudowaną obsługą dokumentów JSON, analizowania i serializacja
  - Obsługuje OAuth 1 i 2, w tym odbiornik przekierowanie lokalnych
  - Nawiązuj kontakty Websockets względem usługi zdalnej
  - W pełni asynchroniczne zadanie interfejsu API oparte na PPL, łącznie z wbudowanej puli wątków

  Obsługuje Windows Desktop (7 i nowsze), Windows Server (2012 i nowsze), Universal Windows Platform, systemu Linux, OSX, Android i iOS.

- [Windows::Web::Http::HttpClient](/uwp/api/windows.web.http.httpclient)

  Klasa klienta HTTP środowiska wykonawczego Windows wzorowana na klasę .NET Framework o tej samej nazwie w przestrzeni nazw System.Web. `HttpClient` w pełni obsługuje asynchroniczne przekazywanie i pobieranie przez HTTP oraz filtry potoku, które umożliwiają wstawianie niestandardowych programów obsługi HTTP do potoku. Zestaw Windows SDK zawiera przykładowe filtry dla mierzonych sieci, uwierzytelnianiem OAuth i inne. W przypadku aplikacji, których platformą docelową tylko Universal Windows Platform, zaleca się używanie `Windows::Web:HttpClient` klasy.

- [Interfejs IXMLHTTPRequest2](/windows/desktop/api/msxml6/nn-msxml6-ixmlhttprequest2)

  Zapewnia macierzysty interfejs COM, że w aplikacji środowiska wykonawczego Windows lub aplikacje pulpitu Windows umożliwiają połączenie z Internetem za pośrednictwem protokołu HTTP i elementu GET, PUT i innych poleceń protokołu HTTP. Aby uzyskać więcej informacji, zobacz [instruktażu: Łączenie za pomocą zadań i żądań XML HTTP](../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md).

- [Windows Internet (WinInet)](/windows/desktop/WinInet/portal)

  Interfejs API Windows, który można użyć w aplikacjach komputerowych Windows, aby nawiązać połączenie z Internetem.

## <a name="see-also"></a>Zobacz także

[Visual C++](../overview/visual-cpp-in-visual-studio.md) <br/>
[Sieci i usług sieci web](/windows/uwp/networking/)
