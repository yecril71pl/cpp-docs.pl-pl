---
title: Aplikacje klasyczne (Visual C++)
ms.date: 11/04/2016
ms.assetid: a020b534-293c-44e2-aa48-516c43ddeb8f
ms.openlocfilehash: 1242878c6b79616aaadb6a176cd29deeb89a7daf
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59033120"
---
# <a name="desktop-applications-visual-c"></a>Aplikacje klasyczne (Visual C++)

A *aplikacja komputerowa* w języku C++ jest natywna aplikacja, które ma dostęp do pełnego zestawu interfejsów API Windows i albo działa w oknie lub w konsoli programu system. Aplikacji klasycznych w języku C++ uruchomić na Windows XP do systemu Windows 10 (chociaż Windows XP nie jest już oficjalnie obsługiwany wiąże się z wielu interfejsów API Windows, które zostały wprowadzone od tego czasu).

Aplikacja komputerowa różni się od aplikacji uniwersalnych platformy Windows (UWP), które mogą być uruchamiane na komputerach z systemem Windows 10, a także na konsoli XBox, Windows Phone, urządzeniu Surface Hub i innych urządzeń. Aby uzyskać więcej informacji na temat klasycznych programu vs. Aplikacje platformy uniwersalnej systemu Windows, zobacz [wybierz swoją technologię](/windows/desktop/choose-your-technology).

### <a name="desktop-bridge"></a>Desktop Bridge

W systemie Windows 10 można pakietu istniejących aplikacji pulpitu lub obiektu COM jako aplikację platformy uniwersalnej systemu Windows i Dodaj funkcje platformy uniwersalnej systemu Windows, takie jak touch lub wywoływać interfejsy API z nowoczesnych zestawu Windows API. Aplikacja platformy uniwersalnej systemu Windows można również dodać do pulpitu rozwiązania w programie Visual Studio i pakiet je razem w jednym pakietu i komunikować się między nimi za pomocą interfejsów API Windows.

W Visual Studio 2017 w wersji 15.4 lub nowszy można utworzyć projekt pakietu aplikacji Windows, do znacznego uproszczenia pracy pakowania swoją istniejącą aplikację pulpitu. Kilka ograniczenia mają zastosowanie w odniesieniu do rejestru, które wywołuje lub korzysta z interfejsów API aplikacji pulpitu, ale w wielu przypadkach można utworzyć ścieżki alternatywnej kodu do osiągnięcia podobne funkcje podczas uruchamiania w pakiecie aplikacji. Aby uzyskać więcej informacji, zobacz [Desktop Bridge](/windows-uwp/porting/desktop-to-uwp-root).

### <a name="terminology"></a>Terminologia

- A *Win32* aplikacja jest Windows, aplikacji klasycznych w języku C++, który może zgłaszać korzystać z natywnych [interfejsów API języka C Windows i/lub interfejsów API modelu COM](/windows/desktop/apiindex/windows-api-list) CRT i standardowe biblioteki interfejsów API i 3 bibliotek innych firm. Aplikacja Win32, który działa w oknie wymaga deweloperowi jawnie pracować Windows komunikaty wewnątrz funkcji procedury Windows. Niezależnie od nazwy jest aplikacją systemu Win32 może być kompilowane jako (x86) 32-bitowy lub 64-bitowych (x64) binarny. W programie Visual Studio IDE to samo warunków x86 i Win32.

- [Component Object Model (COM)](/windows/desktop/com/the-component-object-model) jest specyfikacja, która umożliwia programom napisane w różnych językach, aby komunikować się ze sobą. Windows wiele składników są implementowane jako obiekty COM i postępuj zgodnie z standardowe zasady modelu COM do tworzenia obiektów interfejsu zniszczenie odnajdywania i obiektu.  Obiekty COM z aplikacji klasycznych w języku C++ jest stosunkowo prosta, ale zapisywania obiektu COM jest bardziej zaawansowane. [Active Template Library (ATL)](../atl/atl-com-desktop-components.md) zawiera makra i funkcje pomocnicze, które upraszczają programowanie COM.

- Aplikacja MFC jest używanego przez aplikację pulpitu Windows [Microsoft Foundation Classes](../mfc/mfc-desktop-applications.md) do tworzenia interfejsu użytkownika. Aplikacja MFC umożliwia również składników COM, a także CRT i standardowych interfejsów API w bibliotece. Biblioteka MFC zawiera alokowania elastycznego otok obiektowy C++ przez API Windows i pętli komunikatów okien. MFC jest opcją domyślną dla aplikacji — zwłaszcza aplikacji typu korporacyjnego — które mają wiele formantów interfejsu użytkownika lub niestandardowych formantów użytkownika. MFC udostępnia wygodne klasy pomocnika do zarządzania systemem Windows, serializacji, operacji na tekście, drukowania i elementy interfejsu użytkownika modern, takie jak wstążki. Zaczęła obowiązywać z MFC, należy zapoznać się z systemu Win32.

- A C++/rozszerzenia korzysta z interfejsu wiersza polecenia aplikacji lub składnika C++ składni (zgodnie z C++ specyfikacji) umożliwiające interakcje między kodu .NET i natywnego języka C ++.  A C++/aplikacja interfejsu wiersza polecenia może mieć części, które działa natywnie i części, działających w .NET Framework z dostępem do Biblioteka klasy podstawowej platformy .NET. C++/ Interfejs wiersza polecenia jest preferowaną opcją w przypadku natywnych C++ kod, który musi współpracować przy użyciu kodu napisanego w C# lub Visual Basic. Jest przeznaczona głównie do użytku w bibliotekach DLL platformy .NET, a nie w kodzie interfejsu użytkownika. Aby uzyskać więcej informacji, zobacz [.NET, programowanie za pomocą C++sposób niezamierzony (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md).

Można użyć dowolnej aplikacji klasycznych w języku C++, C Runtime (CRT) i standardową bibliotekę klas i funkcji, obiektów COM i funkcji Windows publicznych, które są łącznie znane jako interfejsu API Windows. Aby zapoznać się z wprowadzeniem do Windows aplikacji klasycznych w języku C++, zobacz [wprowadzenie Win32 i C++](/windows/desktop/LearnWin32/learn-to-program-for-windows).

## <a name="in-this-section"></a>W tej sekcji

|Tytuł|Opis|
|-----------|-----------------|
|[Aplikacje konsoli systemu Windows w języku C++](console-applications-in-visual-cpp.md)|Zawiera informacje o aplikacjach konsoli. Aplikacja konsoli Win32 (lub Win64) ma, nie własnego okna ani pętli komunikatów. Działa w oknie konsoli, a dane wejściowe i wyjściowe są obsługiwane za pośrednictwem wiersza polecenia.|
|[Przewodnik: tworzenie aplikacji klasycznych systemu Windows (C++)](walkthrough-creating-windows-desktop-applications-cpp.md)|Utwórz prostą aplikację pulpitu Windows.|
|[Tworzenie pustej aplikacji klasycznej systemu Windows](creating-an-empty-windows-desktop-application.md)|Jak utworzyć projekt pulpitu Windows, który nie ma żadnych plików domyślne.|
|[Dodawanie plików do pustych aplikacji Win32](adding-files-to-an-empty-win32-applications.md)|Jak dodać pliki do pustego projektu.|
|[Praca z plikami zasobów](working-with-resource-files.md)|Jak dodać obrazy, ikony, tabele ciągów i innych zasobów do aplikacji klasycznej.|
|[Zasoby służące do tworzenia gier za pomocą programu DirectX (C++)](resources-for-creating-a-game-using-directx.md)|Zawiera łącza do zawartości do tworzenia gier w języku C++.|
|[Przewodnik: Tworzenie i używanie biblioteki statycznej](walkthrough-creating-and-using-a-static-library-cpp.md)|Jak utworzyć plik binarny lib.|
|[Instrukcje: używanie zestawu SDK systemu Windows 10 w aplikacji klasycznej systemu Windows](how-to-use-the-windows-10-sdk-in-a-windows-desktop-application.md)|Zawiera instrukcje dotyczące konfigurowania projektu kompilować przy użyciu zestawu SDK systemu Windows 10.|

## <a name="related-articles"></a>Powiązane artykuły

|Tytuł|Opis|
|-----------|-----------------|
|[Tworzenie aplikacji dla systemu Windows](/windows/desktop/index)|Zawiera informacje o interfejsie Windows API i modelu COM. (Niektóre interfejsy API Windows i biblioteki DLL innych firm, są implementowane jako obiekty COM.)|
|[Hilo: Projektowanie aplikacji C++ dla Windows 7](https://msdn.microsoft.com/library/windows/desktop/ff708696.aspx)|Opisuje sposób tworzenia aplikacji klasycznych Windows wzbogaconego klienta używającej animacji Windows i Direct2D do utworzenia interfejsu użytkownika opartego na karuzeli.  W tym samouczku nie został jeszcze zaktualizowany od Windows 7, ale nadal zapewnia szczegółowe wprowadzenie do programowania systemu Win32.|
|[Omówienie programowania w systemie Windows w języku C++](overview-of-windows-programming-in-cpp.md)|W tym artykule opisano najważniejsze funkcje pulpitu Windows programowania w języku C++.|

## <a name="see-also"></a>Zobacz także

[Visual C++](../overview/visual-cpp-in-visual-studio.md)