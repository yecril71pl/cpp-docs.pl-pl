---
title: Chmury i sieci Web programowania w języku Visual C++ | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-azure
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: b63611f1-9723-44d0-ba7f-c3ebef341313
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 360404530df8d07a3cd8fc35654c0c9563ae29fe
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32412403"
---
# <a name="cloud-and-web-programming-in-visual-c"></a>Programowanie chmury i sieci Web w programie Visual C++

W języku C++ masz kilka opcji łączenia się z sieci web i chmury.

## <a name="cloud-programming-options"></a>Opcje programowania w chmurze

- [Windows Azure Mobile Services](http://www.windowsazure.com/develop/mobile/)

   Udostępnia macierzystych interfejsów API, pomocne w aplikacji uniwersalnych platformy systemu Windows (UWP) lub aplikacji klasycznych systemu Windows do nawiązania połączenia usług mobilnych Microsoft Azure. Chociaż większość przykładów w witrynie sieci Web w języku C#, można również użyć C++. Aby uzyskać więcej informacji, zobacz [Szybki Start: Dodawanie usługi mobilnej przy użyciu języka C++](http://msdn.microsoft.com/library/windows/apps/dn263181.aspx).

- [Biblioteka klienta usługi Microsoft Azure Storage dla języka C++](https://blogs.msdn.microsoft.com/windowsazurestorage/2015/04/29/microsoft-azure-storage-client-library-for-c-v1-0-0-general-availability/)

   Biblioteka klienta magazynu Azure dla języka C++ zapewnia kompleksowe interfejsu API do pracy z usługą Azure storage, w tym między innymi następujące możliwości:

  - Tworzenia, odczytu, usuwania i listy kontenerów obiektów blob, tabel i kolejek.
  - Tworzenie, Odczyt, Usuń listę i kopiowania obiektów blob oraz Odczyt i zapis zakresów obiektów blob.
  - Wstaw, Usuń Zamień, scalania i jednostek zapytania w tabeli platformy Azure.
  - Umieścić w kolejce i usuwania z kolejki wiadomości w kolejce systemu Azure.
  - Opóźnieniem listy kontenerów, obiektów blob, tabel i kolejek i opóźnieniem zapytanie jednostek

- [Interfejs API usługi OneDrive](https://dev.onedrive.com/README.htm)

   Interfejs API usługi OneDrive zapewnia zbiór usług HTTP, aby połączyć aplikację do plików i folderów w usłudze Office 365 i SharePoint Server 2016.

- [C++ REST SDK (nazwa kodowa "Casablanca")](https://github.com/Microsoft/cpprestsdk)

   Udostępnia nowoczesnych, między platformami, asynchronicznego interfejsu API do interakcji z usługami REST.

  - Wykonywania wywołań REST względem dowolnego serwera HTTP, dzięki wbudowanej obsłudze analizowania dokument JSON i serializacja
  - Obsługuje OAuth 1 i 2, w tym odbiornika lokalnego przekierowania
  - Nawiązywać połączenia Websocket względem usługi zdalnej
  - Pełni asynchroniczne zadanie oparte na PPL, w tym wbudowane puli wątków interfejsu API

   Obsługuje pulpitu systemu Windows (7 +), Windows Server (2012 +), platformy uniwersalnej systemu Windows, Linux, OS x, Android i iOS. 

- [Windows::Web::http::HttpClient](https://msdn.microsoft.com/en-us/library/windows/apps/windows.web.http.httpclient.aspx)

   Klasa klienta HTTP środowiska wykonawczego systemu Windows w modelu o tej samej nazwie w przestrzeni nazw System.Web klasy .NET Framework. `HttpClient` pełni asynchroniczne obsługuje przekazywanie i pobieranie za pośrednictwem protokołu HTTP i filtry potoku, umożliwiające dodanie niestandardowe programy obsługi HTTP z potokiem. Zestaw Windows SDK zawiera przykładowe filtry dla naliczane sieci, uwierzytelnianie OAuth i inne. Dla aplikacji, które są przeznaczone tylko platformy uniwersalnej systemu Windows, firma Microsoft zaleca się używanie `Windows::Web:HttpClient` klasy. 

- [IXMLHTTPRequest2 — interfejs](http://msdn.microsoft.com/library/windows/apps/hh831151.aspx)

   Udostępnia natywnego interfejsu COM w aplikacjach środowiska wykonawczego systemu Windows lub aplikacji klasycznych systemu Windows umożliwiają połączenie z Internetem za pośrednictwem protokołu HTTP, a UZYSKAĆ problem, PUT i innych poleceń HTTP. Aby uzyskać więcej informacji, zobacz [wskazówki: łączenie za pomocą zadań i żądań XML HTTP](../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md).

- [Windows Internet (WinInet)](http://msdn.microsoft.com/library/windows/desktop/aa385331\(v=vs.85\).aspx)

   Interfejs API systemu Windows, który można użyć w aplikacji klasycznych systemu Windows, aby nawiązać połączenie z Internetem.

## <a name="see-also"></a>Zobacz także

[Visual C++](../visual-cpp-in-visual-studio.md) <br/>
[Sieci i usług sieci web](/windows/uwp/networking/)
