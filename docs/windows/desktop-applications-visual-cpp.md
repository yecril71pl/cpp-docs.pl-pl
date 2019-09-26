---
title: Aplikacje klasyczne (wizualizacja C++)
ms.date: 07/28/2019
ms.assetid: a020b534-293c-44e2-aa48-516c43ddeb8f
ms.topic: overview
ms.openlocfilehash: 91fcc596a4c30e3fa74043c846eda6f06b666f2c
ms.sourcegitcommit: 7750e4c291d56221c8893120c56a1fe6c9af60d6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274725"
---
# <a name="desktop-applications-visual-c"></a>Aplikacje klasyczne (wizualizacja C++)

*Aplikacja klasyczna* w C++ programie to Natywna aplikacja, która może uzyskiwać dostęp do pełnego zestawu interfejsów API systemu Windows i jest uruchamiana w oknie lub w konsoli systemowej. Aplikacje klasyczne programu C++ mogą działać w systemie Windows XP za poorednictwem systemu Windows 10 (mimo że system Windows XP nie jest już oficjalnie obsługiwany i istnieje wiele interfejsów API systemu Windows, które zostały wprowadzone od tej pory). 

Aplikacja klasyczna różni się od aplikacji platforma uniwersalna systemu Windows (platformy UWP), która może być uruchamiana na komputerach z systemem Windows 10, a także na konsolach XBox, Windows Phone, Surface Hub i innych urządzeniach. Więcej informacji o programie Desktop a PLATFORMY UWP aplikacje, zobacz [Wybierz swoją technologię](/windows/win32/choose-your-technology).

### <a name="desktop-bridge"></a>Mostek Desktop

W systemie Windows 10 istnieje możliwość spakowania istniejącej aplikacji klasycznej lub obiektu COM jako aplikacji platformy UWP oraz dodania funkcji platformy UWP, takich jak Touch, lub wywołania interfejsów API z zestawu nowoczesnych interfejsów API systemu Windows. Możesz również dodać aplikację platformy UWP do rozwiązania pulpitu w programie Visual Studio i spakować je razem w jednym pakiecie i używać interfejsów API systemu Windows do komunikacji między nimi.

W programie Visual Studio 2017 w wersji 15,4 lub nowszej można utworzyć projekt pakietu aplikacji systemu Windows, aby znacznie uprościć pracę nad pakowaniem istniejącej aplikacji klasycznej. Istnieją pewne ograniczenia dotyczące tego, jakie są wywołania rejestru lub interfejsy API używane przez aplikację klasyczną, ale w wielu przypadkach można utworzyć alternatywne ścieżki kodu, aby osiągnąć podobną funkcjonalność podczas działania w pakiecie aplikacji. Aby uzyskać więcej informacji, zobacz [mostek Desktop](/windows/uwp/porting/desktop-to-uwp-root).

### <a name="terminology"></a>Terminologia

- Aplikacja *Win32* to aplikacja klasyczna systemu Windows w C++ systemie, która może korzystać z natywnych interfejsów API [systemu Windows C i/lub](/windows/win32/apiindex/windows-api-list) interfejsów API języka c++ oraz interfejsów API biblioteki standardowej i bibliotek innych firm. Aplikacja Win32 uruchamiana w oknie wymaga, aby deweloper działał jawnie z komunikatami systemu Windows w ramach funkcji procedury systemu Windows. Pomimo nazwy, aplikacja Win32 może być skompilowana jako plik binarny 32-bitowy (x86) lub 64-bitowy (x64). W środowisku IDE programu Visual Studio warunki x86 i Win32 są synonimami.

- [Component Object Model (com)](/windows/win32/com/the-component-object-model) to specyfikacja, która umożliwia programom w różnych językach komunikowanie się ze sobą. Wiele składników systemu Windows jest implementowanych jako obiekty COM i są zgodne ze standardowymi regułami COM na potrzeby tworzenia obiektów, odnajdywania interfejsów i niszczenia obiektów.  Używanie obiektów COM z C++ aplikacji klasycznych jest stosunkowo proste, ale pisanie własnego obiektu com jest bardziej zaawansowane. [Active Template Library (ATL)](../atl/atl-com-desktop-components.md) zawiera makra i funkcje pomocnika, które upraszczają programowanie com.

- Aplikacja MFC jest aplikacją klasyczną systemu Windows, która używa [Microsoft Foundation Classes](../mfc/mfc-desktop-applications.md) do tworzenia interfejsu użytkownika. Aplikacja MFC może również używać składników COM oraz interfejsów API CRT i Standard Library. MFC udostępnia cienkie C++ , zorientowane obiektowo otokę na pętlę komunikatów okna i interfejsy API systemu Windows. MFC jest domyślnym wyborem dla aplikacji — w szczególności aplikacji typu Enterprise — obejmujących wiele kontrolek interfejsu użytkownika lub niestandardowych kontrolek użytkownika. MFC udostępnia wygodne klasy pomocnicze do zarządzania oknem, serializacji, manipulowania tekstem, drukowania oraz elementów interfejsu użytkownika Modern, takich jak Wstążka. Aby obowiązywać z MFC, należy zapoznać się z Win32.

- Aplikacja C++/CLI lub składnik używa rozszerzeń do C++ składni (jak jest to C++ dozwolone przez standard) w celu umożliwienia interakcji między platformą .NET i natywnym kodem języka C + +.  Aplikacja C++/CLI może mieć części, które działają natywnie i części, które działają w .NET Framework z dostępem do biblioteki klas bazowych platformy .NET. C++/CLI jest preferowaną opcją w przypadku kodu natywnego C++ , który musi pracować z kodem zapisanym C# lub Visual Basic. Jest ona przeznaczona do użycia w bibliotekach DLL platformy .NET, a nie w kodzie interfejsu użytkownika. Aby uzyskać więcej informacji, zobacz [programowanie .NET C++przy użyciu/CLI C++(Visual)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md).

Dowolna aplikacja klasyczna w programie C++ może korzystać z klas środowiska uruchomieniowego języka C (CRT) i bibliotek standardowej biblioteki oraz funkcji, obiektów com i publicznych funkcji systemu Windows, które są nazywane ZBIORCZo interfejsem API systemu Windows. Aby zapoznać się z wprowadzeniem do aplikacji C++klasycznych systemu Windows w systemie, zobacz Wprowadzenie do [systemu Win32 i C++ ](/windows/win32/LearnWin32/learn-to-program-for-windows).

## <a name="in-this-section"></a>W tej sekcji

|Tytuł|Opis|
|-----------|-----------------|
|[Aplikacje konsoli systemu Windows w języku C++](console-applications-in-visual-cpp.md)|Zawiera informacje o aplikacjach konsoli. Aplikacja konsolowa Win32 (lub win64) nie ma własnego okna i nie zawiera pętli komunikatów. Działa w oknie konsoli, a dane wejściowe i wyjściowe są obsługiwane za pomocą wiersza polecenia.|
|[Przewodnik: tworzenie aplikacji klasycznych systemu Windows (C++)](walkthrough-creating-windows-desktop-applications-cpp.md)|Utwórz prostą aplikację klasyczną systemu Windows.|
|[Tworzenie pustej aplikacji klasycznej systemu Windows](creating-an-empty-windows-desktop-application.md)|Jak utworzyć projekt pulpitu systemu Windows, który nie ma plików domyślnych.|
|[Dodawanie plików do pustych aplikacji Win32](adding-files-to-an-empty-win32-applications.md)|Jak dodać pliki do pustego projektu.|
|[Praca z plikami zasobów](working-with-resource-files.md)|Jak dodać obrazy, ikony, tabele ciągów i inne zasoby do aplikacji klasycznej.|
|[Zasoby służące do tworzenia gier za pomocąC++programu DirectX ()](resources-for-creating-a-game-using-directx.md)|Linki do zawartości na potrzeby tworzenia gier C++w programie.|
|[Przewodnik: Tworzenie i używanie biblioteki statycznej](walkthrough-creating-and-using-a-static-library-cpp.md)|Jak utworzyć plik binarny. lib.|
|[Instrukcje: używanie zestawu SDK systemu Windows 10 w aplikacji klasycznej systemu Windows](how-to-use-the-windows-10-sdk-in-a-windows-desktop-application.md)|Zawiera kroki konfigurowania projektu do kompilowania przy użyciu zestawu SDK systemu Windows 10.|

## <a name="related-articles"></a>Powiązane artykuły

|Tytuł|Opis|
|-----------|-----------------|
|[Tworzenie aplikacji dla systemu Windows](/windows/win32/index)|Zawiera informacje o interfejsie API systemu Windows i modelu COM. (Niektóre interfejsy API systemu Windows i biblioteki DLL innych firm są implementowane jako obiekty COM).|
|[Hilo Opracowywanie C++ aplikacji dla systemu Windows 7](https://msdn.microsoft.com/library/windows/desktop/ff708696.aspx)|Opisuje sposób tworzenia rozbudowanej aplikacji klasycznej systemu Windows, która używa animacji systemu Windows i Direct2D do tworzenia interfejsu użytkownika opartego na karuzeli.  Ten samouczek nie został zaktualizowany od systemu Windows 7, ale nadal zawiera szczegółowe wprowadzenie do programowania Win32.|
|[Omówienie programowania w systemie Windows w języku C++](overview-of-windows-programming-in-cpp.md)|Zawiera opis najważniejszych funkcji programowania komputerów z systemem C++Windows w systemie.|

## <a name="see-also"></a>Zobacz także

[Język C++ w programie Visual Studio](../overview/visual-cpp-in-visual-studio.md)