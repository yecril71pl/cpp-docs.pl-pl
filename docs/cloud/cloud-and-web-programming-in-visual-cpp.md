---
title: Programowanie chmury i sieci Web w programie Visual C++
ms.date: 05/14/2019
ms.assetid: b63611f1-9723-44d0-ba7f-c3ebef341313
ms.topic: overview
ms.openlocfilehash: 675502e9ae50c9e69ad4555502000d128d5d4cbe
ms.sourcegitcommit: efc8c32205c9d610f40597556273a64306dec15d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/26/2020
ms.locfileid: "88898674"
---
# <a name="cloud-and-web-programming-in-visual-c"></a>Programowanie chmury i sieci Web w programie Visual C++

W języku C++ istnieje kilka opcji nawiązywania połączenia z siecią Web i chmurą.

## <a name="microsoft-azure-sdks-and-rest-services"></a>Microsoft Azure zestawy SDK i usługi REST

- [Microsoft Azure Storage Biblioteka kliencka dla języka C++](https://azure.github.io/azure-storage-cpp/)

  Biblioteka klienta usługi Azure Storage dla języka C++ zapewnia kompleksowy interfejs API do pracy z usługą Azure Storage, w tym m.in. następujące możliwości:

  - Tworzenie, odczytywanie, usuwanie i wyświetlanie listy kontenerów obiektów blob, tabel i kolejek.
  - Tworzenie, odczytywanie, usuwanie, wyświetlanie i kopiowanie obiektów blob oraz odczytywanie i zapisywanie zakresów obiektów BLOB.
  - Wstawianie, usuwanie, zastępowanie, scalanie i wykonywanie zapytań względem jednostek w tabeli platformy Azure.
  - Kolejkowanie i dekolejkowanie komunikatów w kolejce platformy Azure.
  - Opóźnieniem listy kontenerów, obiektów blob, tabel i kolejek oraz jednostek zapytań opóźnieniem

- [Zestawy SDK ANSI C99 Azure IoT Hub](/azure/iot-hub/iot-hub-devguide-sdks) dla Internet rzeczy umożliwiają uruchamianie aplikacji IoT na urządzeniu lub w zapleczu.

- [Usługi OneDrive i SharePoint w Microsoft Graph](https://dev.onedrive.com/README.htm)

  Interfejs API usługi OneDrive udostępnia zestaw usług HTTP, aby połączyć aplikację z plikami i folderami w Microsoft 365 i SharePoint Server 2016.

## <a name="windows-and-cross-platform-networking-apis"></a>Interfejsy API sieci dla wielu platform

- [C++ REST SDK (nazwa kodowa "Casablanca")](https://github.com/Microsoft/cpprestsdk)

  Zapewnia nowoczesny, międzyplatformowy, asynchroniczny interfejs API do współpracy z usługami REST.

  - Wykonaj wywołania REST dla dowolnego serwera HTTP z wbudowaną obsługą analizy dokumentu JSON i serializacji
  - Obsługuje uwierzytelnianie OAuth 1 i 2, łącznie z odbiornikiem lokalnego przekierowania
  - Tworzenie połączeń obiektów WebSockets z usługami zdalnymi
  - W pełni asynchroniczny interfejs API zadań oparty na PPL, łącznie z wbudowaną pulą wątków

  Obsługuje Pulpity systemu Windows (7 +), Windows Server (2012 +), platforma uniwersalna systemu Windows, Linux, OSX, Android i iOS.

- [Windows:: Web:: http:: HttpClient](/uwp/api/windows.web.http.httpclient)

  Klasa klienta HTTP środowisko wykonawcze systemu Windows modelowana w klasie .NET Framework o tej samej nazwie w przestrzeni nazw System. Web. `HttpClient` w pełni obsługuje asynchroniczne przekazywanie i pobieranie za pośrednictwem protokołu HTTP oraz filtry potokowe, które umożliwiają wstawianie niestandardowych programów obsługi HTTP do potoku. Windows SDK zawiera przykładowe filtry dla sieci taryfowych, uwierzytelniania OAuth i nie tylko. W przypadku aplikacji przeznaczonych tylko do platforma uniwersalna systemu Windows zalecamy użycie `Windows::Web:HttpClient` klasy.

- [IXMLHTTPRequest2, interfejs](/windows/win32/api/msxml6/nn-msxml6-ixmlhttprequest2)

  Zapewnia natywny interfejs COM, którego można używać w aplikacjach środowisko wykonawcze systemu Windows lub aplikacjach klasycznych systemu Windows do łączenia się z Internetem za pośrednictwem protokołu HTTP i wydawania poleceń GET, PUT i innych. Aby uzyskać więcej informacji, zobacz [Przewodnik: Łączenie przy użyciu zadań i żądań HTTP XML](../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md).

- [Internet Windows (WinInet)](/windows/win32/WinInet/portal)

  Interfejs API systemu Windows, który może być używany w aplikacjach klasycznych systemu Windows do łączenia się z Internetem.

## <a name="see-also"></a>Zobacz też

[Język C++ w programie Visual Studio](../overview/visual-cpp-in-visual-studio.md) <br/>
[Centrum deweloperów Microsoft Azure C i C++](https://azure.microsoft.com/develop/cpp/) <br/>
[Sieci i usługi sieci Web (platformy UWP)](/windows/uwp/networking/)
