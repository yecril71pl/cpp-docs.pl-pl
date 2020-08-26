---
title: Narzędzia i funkcje języka C++ w wersjach programu Visual Studio
ms.date: 05/21/2019
helpviewer_keywords:
- tools and platforms [C++]
ms.assetid: 3d88607b-9cc4-490a-8d4c-31ee7610a26f
ms.openlocfilehash: 00c096203ae056c96c87d67a491d3c84b3d1fb3a
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88845357"
---
# <a name="c-tools-and-features-in-visual-studio-editions"></a>Narzędzia i funkcje języka C++ w wersjach programu Visual Studio

::: moniker range=">=vs-2019"

W programie Visual Studio 2019 dostępne są następujące funkcje języka C++. O ile nie określono inaczej, wszystkie funkcje są dostępne we wszystkich wersjach: Visual Studio Community, Visual Studio Professional i Visual Studio Enterprise. Niektóre funkcje wymagają określonych obciążeń lub składników opcjonalnych, które można zainstalować za pomocą Instalator programu Visual Studio.

## <a name="platforms"></a>Platformy

- Pulpit systemu Windows
- Platforma uniwersalna systemu Windows ((tablet, komputery, Xbox, IoT i HoloLens))
- Linux
- Android
- iOS

## <a name="compilers"></a>Kompilatory

- MSVC 32 — bitowy kompilator dla procesorów x86, x64, ARM i ARM64
- MSVC 64 — bitowy kompilator dla procesorów x86, x64, ARM i ARM64
- Kompilator międzybranżowy dla usługi ARM
- Clang/LLVM
  - W systemie Windows, Clang/LLVM 7,0, przeznaczony dla architektury x86 lub x64 (tylko obsługa CMake). Inne wersje Clang mogą funkcjonować, ale nie są oficjalnie obsługiwane.
  - W systemie Linux wszystkie instalacje Clang/LLVM obsługiwane przez dystrybucji.

## <a name="c-workloads"></a>Obciążenia języka C++

Program Visual Studio zawiera następujące obciążenia do programowania w języku C++. Można zainstalować dowolne lub wszystkie z nich wraz z innymi obciążeniami, takimi jak programowanie aplikacji klasycznych platformy .NET, programowanie w języku Python, programowanie na platformie Azure, programowanie rozszerzeń Visual Studio i inne.

### <a name="desktop-development-with-c"></a>Programowanie aplikacji klasycznych w języku C++

Uwzględnione

- Podstawowe funkcje pulpitu języka C++

Składniki opcjonalne:

- MSVC v142-VS 2019 C++ x64/x86 Build Tools (v 14.21)
- Zestaw SDK systemu Windows 10 (10.0.17763.0)
- Debuger just in Time
- Narzędzia profilowania języka C++
- C++ CMake Tools dla systemu Windows
- C++ ATL dla narzędzi kompilacji v142 (x86 & x64)
- Adapter testowy do zwiększenia. test
- Test Adapter for Google Test
- Live Share
- IntelliCode
- IntelliTrace (tylko w przedsiębiorstwie)
- C++ MFC for v142 Build Tools (x86 & x64)
- Obsługa języka C++/CLI dla narzędzi kompilacji v142 (14,21)
- Moduły C++ dla narzędzi do kompilacji v142 (x64/x86 — eksperymentalne)
- Kompilator Clang dla systemu Windows
- IncrediBuild — przyspieszanie kompilacji
- Zestaw SDK systemu Windows 10 (10.0.17134.0)
- Zestaw SDK systemu Windows 10 (10.0.16299.0)
- MSVC najnowsze 141-VS 2017 C++ x64/x86 Build Tools (v 14.16)
- MSVC wersji 140-VS 2015 C++ build Tools (v 14.00)

### <a name="linux-development-with-c"></a>Programowanie dla systemu Linux w języku C++

Uwzględnione

- Podstawowe funkcje języka C++
- Uniwersalne środowisko uruchomieniowe języka C systemu Windows
- Programowanie w języku C++ dla systemu Linux

Składniki opcjonalne:

- C++ CMake Tools dla systemu Linux
- Narzędzia programistyczne Embedded i IoT

### <a name="universal-windows-platform-development"></a>Opracowywanie platforma uniwersalna systemu Windows

Uwzględnione

- Blend for Visual Studio
- .NET Native i .NET Standard
- Menedżer pakietów NuGet
- Narzędzia platforma uniwersalna systemu Windows
- Zestaw SDK systemu Windows 10 (10.0.17763.0)

Składniki opcjonalne:

- IntelliCode
- IntelliTrace (tylko w przedsiębiorstwie)
- Łączność urządzeń USB
- C++ (v142) — narzędzia platforma uniwersalna systemu Windows
- C++ (najnowsze 141) — narzędzia platforma uniwersalna systemu Windows
- Debuger grafiki i Profiler procesora GPU dla programu DirectX
- Zestaw SDK systemu Windows 10 (10.0.18362.0)
- Zestaw SDK systemu Windows 10 (10.0.17134.0)
- Zestaw SDK systemu Windows 10 (10.0.16299.0)
- Narzędzia architektury i analizy

### <a name="c-game-development"></a>Programowanie gier w języku C++

Uwzględnione

- Podstawowe funkcje języka C++
- Uniwersalne środowisko uruchomieniowe języka C systemu Windows
- Aktualizacja pakietu redystrybucyjnego języka C++ 2019
- MSVC v142-VS 2019 C++ x64/x86 Build Tools (v 14.21)

Składniki opcjonalne:

- Narzędzia profilowania języka C++
- Zestaw SDK systemu Windows 10 (10.0.17763.0)
- IntelliCode
- IntelliTrace (tylko w przedsiębiorstwie)
- Zestaw SDK systemu Windows 10 (10.0.17134.0)
- Zestaw SDK systemu Windows 10 (10.0.16299.0)
- IncrediBuild — przyspieszanie kompilacji
- Cocos
- Instalator aparatu Unreal
- Obsługa środowiska IDE systemu Android dla aparatu Unreal

### <a name="mobile-development-with-c"></a>Tworzenie aplikacji mobilnych w języku C++

Uwzględnione

- Podstawowe funkcje języka C++
- Konfiguracja Android SDK (poziom interfejsu API 25) (lokalna instalacja na potrzeby opracowywania aplikacji mobilnych za pomocą języka C++)

Składniki opcjonalne:

- Android NDK (R16B)
- Apache Ant (1.9.3)
- Narzędzia programistyczne w języku C++ dla systemu Android
- IntelliCode
- Google Emulator systemu Android (poziom interfejsu API 25) (Instalacja lokalna)
- Intel Hardware Accelerated Execution Manager (HAXM) (Instalacja lokalna)
- Android NDK (R16B) (32-bitowe)
- Narzędzia programistyczne w języku C++ dla systemu iOS
- IncrediBuild — przyspieszanie kompilacji

## <a name="individual-components"></a>Poszczególne składniki

Te składniki można zainstalować niezależnie od dowolnego obciążenia.

- Diagnostyka JavaScript
- Live Share
- Środowisko uruchomieniowe języka C++ platforma uniwersalna systemu Windows dla narzędzi kompilacji v142
- Publikowanie ClickOnce
- Projekty Instalatora Microsoft Visual Studio

## <a name="libraries-and-headers"></a>Biblioteki i nagłówki

- Nagłówki i biblioteki systemu Windows
- Uniwersalne środowisko uruchomieniowe języka C systemu Windows (CRT)
- Standardowa biblioteka C++
- ATL
- MFC
- Biblioteka klas programu .NET Framework
- Biblioteka obsługi języka C++ dla platformy .NET
- OpenMP 2,0
- Ponad 900 bibliotek Open Source za pośrednictwem wykazu vcpkg

## <a name="build-and-project-systems"></a>Systemy kompilacji i projektu

- CMake
- Dowolny system kompilacji za pośrednictwem otwartego folderu
- Kompilacje w wierszu polecenia (msbuild.exe)
- Natywne wiele elementów docelowych
- Zarządzane wiele elementów docelowych
- Kompilacje równoległe
- Dostosowywanie kompilacji
- Rozszerzalność stron właściwości

## <a name="project-templates"></a>Szablony projektów

Następujące szablony projektów są dostępne w zależności od zainstalowanych obciążeń.

Pulpit systemu Windows:

- Pusty projekt
- Aplikacja konsolowa
- Kreator pulpitu systemu Windows
- Aplikacja klasyczna systemu Windows
- Projekt elementów udostępnionych
- Aplikacja MFC
- Biblioteka dołączana dynamicznie
- Pusty projekt CLR
- Aplikacja konsolowa CLR
- Biblioteka statyczna
- Projekt CMake
- Projekt ATL
- Biblioteka dołączana dynamicznie MFC
- Biblioteka klas CLR
- Projekt pliku reguł programu make (Windows)
- MFC ActiveXControl
- Natywny projekt testów jednostkowych
- Google Test

Platforma uniwersalna systemu Windows (C++/CX):

- Pusta aplikacja
- Aplikacja DirectX 11 i XAML
- Aplikacja DirectX 11
- Aplikacja DirectX 12
- Aplikacja testów jednostkowych
- DLL
- Składnik środowiska wykonawczego systemu Windows
- Biblioteka statyczna
-  Projekt pakietu aplikacji systemu Windows

W systemie Linux:

- Aplikacja konsolowa (Linux)
- Pusty projekt (Linux)
- Raspberry Pi
- Projekt pliku reguł programu make (Linux)

## <a name="tools"></a>narzędzia

- Łączenie przyrostowe (Link.exe)
- Narzędzie Microsoft Make (Nmake.exe)
- Generator lib (Lib.exe)
- Kompilator zasobów systemu Windows (Rc.exe)
- Konwerter zasobów systemu Windows do obiektów (CvtRes.exe)
- Narzędzie do konserwacji przeglądanych informacji (BscMake.exe)
- Nazwa C++ Undecorator (Undname.exe)
- Zrzutu COFF/PE (Dumpbin.exe)
- Edytor COFF/PE (Editbin.exe)
- MASM (Ml.exe)
- Spy++
- ErrLook
- AtlTrace
- Zasady wnioskowania
- Profilowana Optymalizacja

## <a name="debugging-features"></a>Funkcje debugowania

- Debugowanie natywne
- Natvis (wizualizacja typu natywnego)
- Debugowanie grafiki
- Debugowanie zarządzane
- Użycie procesora GPU
- Użycie pamięci
- Debugowanie zdalne
- Debugowanie SQL
- Statyczna analiza kodu

## <a name="designers-and-editors"></a>Projektanci i edytory

- XAML Designer
- Projektant stylów CSS/Edytor
- Projektant/Edytor HTML
- Edytor XML
-  Edytor kodu źródłowego
- Funkcje produktywności: Refaktoryzacja, EDG aparat IntelliSense, formatowanie kodu C++
- Projektant Windows Forms
- Projektant danych
- Natywny Edytor zasobów (pliki. RC)
- Edytory zasobów
- Edytor modelu
- Projektant cieniowania
- Weryfikacja zależności na żywo (tylko dla przedsiębiorstw)
- Diagramy warstw architektonicznych (tylko dla przedsiębiorstw)
- Sprawdzanie poprawności architektury (tylko dla przedsiębiorstw)
- Klonowanie kodu (tylko dla przedsiębiorstw)

## <a name="data-features"></a>Funkcje danych

- Projektant danych
- Obiekty danych
- Usługi sieci Web
- Eksplorator serwera

## <a name="automation-and-extensibility"></a>Automatyzacja i rozszerzalność

- Modele obiektów rozszerzalności
- Model kodu
- Model projektu
- Model edytora zasobów
- Model Kreatora
- Model obiektów debugera

## <a name="application-lifecycle-management-tools"></a>Narzędzia do zarządzania cyklem życia aplikacji

- Testowanie jednostkowe (Microsoft Native C++, zwiększanie. Testowanie, Google Test, narzędzia ctest)
- Mapa kodu i wykresy zależności (wersje Professional i Enterprise)
- Pokrycie kodu (tylko w przedsiębiorstwie)
- Testowanie ręczne (tylko dla przedsiębiorstw)
- Testowanie poznawcze (tylko dla przedsiębiorstw)
- Zarządzanie przypadkami testowymi (tylko dla przedsiębiorstw)
- Integracja z debugerem mapy kodu (tylko w przedsiębiorstwie)
- Live Unit Testing (tylko w przedsiębiorstwie)
- IntelliTrace (tylko w przedsiębiorstwie)
- IntelliTest (tylko w przedsiębiorstwie)
- Sztuczne firmy Microsoft (izolacja testu jednostkowego) (tylko dla przedsiębiorstw)
- Pokrycie kodu (tylko w przedsiębiorstwie)

## <a name="see-also"></a>Zobacz też

[Instalowanie programu Visual Studio](/visualstudio/install/install-visual-studio)<br/>
[Co nowego w programie Visual Studio](/visualstudio/ide/whats-new-in-visual-studio)<br/>
[Typy projektów C++ w programie Visual Studio](../build/reference/visual-cpp-project-types.md)

::: moniker-end

::: moniker range="<=vs-2017"

W poniższych tabelach przedstawiono funkcje Visual C++, które są dostępne w programie Visual Studio 2017. X w komórce wskazuje, że funkcja jest dostępna; pusta komórka wskazuje, że funkcja jest niedostępna. Uwagi w nawiasach wskazują, że funkcja jest dostępna, ale jest ograniczona.

## <a name="platforms"></a>Platformy

|Platforma|Visual Studio Express dla systemu Windows 10|Visual Studio Express dla komputerów z systemem Windows|Visual Studio Community/Professional|Visual Studio Enterprise|
|-|-|-|-|-|
|Pulpit systemu Windows||X|X|X|
|Platforma uniwersalna systemu Windows (telefony, tablety, komputery, Xbox, IoT i HoloLens))|X||X|X|
|Linux|X|X|
|Microsoft Store 8,1|||X|X|
|Windows Phone 8.0|||X|X|
|Android|||X|X|
|iOS|||X|X|

## <a name="compilers"></a>Kompilatory

|Compiler|Visual Studio Express dla systemu Windows|Visual Studio Express dla komputerów z systemem Windows|Visual Studio Professional/społeczność|Visual Studio Enterprise|
|--------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|MSVC 32-bit x86 — kompilator|X|X|X|X|
|X86_arm kompilatora krzyżowe|X||X|X|
|MSVC 64-bit x64 — kompilator|||X|X|
|Kompilator X86_ x64|X|X|X|X|

## <a name="libraries-and-headers"></a>Biblioteki i nagłówki

|Biblioteka lub nagłówek|Visual Studio Express dla systemu Windows|Visual Studio Express dla komputerów z systemem Windows|Visual Studio Professional/społeczność|Visual Studio Enterprise|
|-----------------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|Nagłówki i biblioteki systemu Windows oraz Biblioteka CRT|Y|X|X|X|
|Standardowa biblioteka C++|X|X|X|X|
|ATL|||X|X|
|MFC|||X|X|
|Biblioteka klas programu .NET Framework||X|X|X|
|Biblioteka obsługi języka C++ dla platformy .NET||X|X|X|
|OpenMP 2,0|X|X|X|X|

## <a name="project-templates"></a>Szablony projektów

|Szablon|Visual Studio Express dla systemu Windows|Visual Studio Express dla komputerów z systemem Windows|Visual Studio Professional/społeczność|Visual Studio Enterprise|
|--------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|Szablony XAML dla platformy UWP, Windows 8.1, Windows Phone 8,0|X||X|X|
|Aplikacja Direct3D|X||X|X|
|Biblioteka DLL (uniwersalna systemu Windows)|X||X|X|
|Biblioteka statyczna (platforma uniwersalna systemu Windows)|X||X|X|
|Składnik środowiska wykonawczego systemu Windows|X||X|X|
|Aplikacja testów jednostkowych (platforma uniwersalna systemu Windows)|X||X|X|
|Projekt ATL|||X|X|
|Biblioteka klas (CLR)||X|X|X|
|Aplikacja konsolowa CLR||X|X|X|
|Pusty projekt CLR||X|X|X|
|Kreator niestandardowy|||X|X|
|Pusty projekt||X|X|X|
|Projekt pliku reguł programu make||X|X|X|
|Kontrolka ActiveX MFC|||X|X|
|Aplikacja MFC|||X|X|
|BIBLIOTEKA DLL MFC|||X|X|
|Projekt testowy|X|X|X|X|
|Aplikacja konsolowa Win32||X|X|X|
|Projekt Win32||X|X|X|

## <a name="tools"></a>narzędzia

|Narzędzie|Visual Studio Express dla systemu Windows|Visual Studio Express dla komputerów z systemem Windows|Visual Studio Professional/społeczność|Visual Studio Enterprise|
|----------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|Łączenie przyrostowe (Link.exe)|X|X|X|X|
|Narzędzie do konserwacji programu (Nmake.exe)||X|X|X|
|Generator lib (Lib.exe)|X|X|X|X|
|Kompilator zasobów systemu Windows (Rc.exe)|X|X|X|X|
|Konwerter zasobów systemu Windows do obiektów (CvtRes.exe)||X|X|X|
|Narzędzie do konserwacji przeglądanych informacji (BscMake.exe)|X|X|X|X|
|Nazwa C++ Undecorator (Undname.exe)|X|X|X|X|
|Zrzutu COFF/PE (Dumpbin.exe)|X|X|X|X|
|Edytor COFF/PE (Editbin.exe)|X|X|X|X|
|MASM (Ml.exe)|||X|X|
|Spy++|||X|X|
|ErrLook|||X|X|
|AtlTrace|||X|X|
|Devenv.com|||X|X|
|Zasady wnioskowania|||X|X|
|Uaktualnij projekty VCBuild. vcproj do programu MSBuild (VCUpgrade.exe)|X|X|X|X|
|Profilowana Optymalizacja|||X|X|

## <a name="debugging-features"></a>Funkcje debugowania

|Funkcja debugowania|Visual Studio Express dla systemu Windows|Visual Studio Express dla komputerów z systemem Windows|Visual Studio Professional/społeczność|Visual Studio Enterprise|
|-----------------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|Debugowanie natywne|X|X|X|X|
|Natvis (wizualizacja typu natywnego)|X|X|X|X|
|Debugowanie grafiki|X||X|X|
|Debugowanie zarządzane||X|X|X|
|Użycie procesora GPU|X||X|X|
|Użycie pamięci|X||X|X|
|Debugowanie zdalne|X|X|X|X|
|Debugowanie SQL|||X|X|
|Statyczna analiza kodu|Ograniczone|Ograniczone|X|X|

## <a name="designers-and-editors"></a>Projektanci i edytory

|Projektant lub Edytor|Visual Studio Express dla systemu Windows|Visual Studio Express dla komputerów z systemem Windows|Visual Studio Professional/społeczność|Visual Studio Enterprise|
|------------------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|XAML Designer|X||X|X|
|Projektant stylów CSS/Edytor|X|X|X|X|
|Projektant/Edytor HTML|X|X|X|X|
|Edytor XML|X|X|X|X|
| Edytor kodu źródłowego|X|X|X|X|
|Funkcje produktywności: Refaktoryzacja, IntelliSense, formatowanie kodu C++|X|X|X|X|
|Projektant Windows Forms||X|X|X|
|Projektant danych|||X|X|
|Natywny Edytor zasobów (pliki. RC)|||X|X|
|Edytory zasobów|X|X|X|X|
|Edytor modelu|X||X|X|
|Projektant cieniowania|X||X|X|

## <a name="data-features"></a>Funkcje danych

|Funkcja danych|Visual Studio Express dla systemu Windows|Visual Studio Express dla komputerów z systemem Windows|Visual Studio Professional/społeczność|Visual Studio Enterprise|
|------------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|Projektant danych|||X|X|
|Obiekty danych|||X|X|
|Usługi sieci Web|||X|X|
|Eksplorator serwera|||X|X|

## <a name="build-and-project-systems"></a>Systemy kompilacji i projektu

|Kompilacja lub funkcja projektu|Visual Studio Express dla systemu Windows|Visual Studio Express dla komputerów z systemem Windows|Visual Studio Professional/społeczność|Visual Studio Enterprise|
|------------------------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|Kompilacje w wierszu polecenia (msbuild.exe)|X|X|X|X|
|Natywne wiele elementów docelowych||X|X|X|
|Zarządzane wiele elementów docelowych||X|X|X|
|Kompilacje równoległe|X|X|X|X|
|Dostosowywanie kompilacji|X|X|X|X|
|Rozszerzalność stron właściwości|X|X|X|X|

## <a name="automation-and-extensibility"></a>Automatyzacja i rozszerzalność

|Automatyzacja i rozszerzalność|Visual Studio Express dla systemu Windows|Visual Studio Express dla komputerów z systemem Windows|Visual Studio Professional/społeczność|Visual Studio Enterprise|
|----------------------------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|Modele obiektów rozszerzalności|||X|X|
|Model kodu|||X|X|
|Model projektu|||X|X|
|Model edytora zasobów|||X|X|
|Model Kreatora|||X|X|
|Model obiektów debugera|||X|X|

## <a name="application-lifecycle-management-tools"></a>Narzędzia do zarządzania cyklem życia aplikacji

|Narzędzie|Visual Studio Express dla systemu Windows|Visual Studio Express dla komputerów z systemem Windows|Visual Studio Professional/społeczność|Visual Studio Enterprise|
|-|-|-|-|-|
|Testy jednostkowe (natywna platforma)|X|X|X|X|
|Testy jednostkowe (struktura zarządzana)||X|X|X|
|Pokrycie kodu||||X|
|Testowanie ręczne||||X|
|Testowanie eksploracyjne||||X|
|Zarządzanie przypadkami testowymi||||X|
|Mapa kodu i wykresy zależności|||tylko do odczytu|X|
|Debugowanie mapy kodu||||X|

## <a name="see-also"></a>Zobacz też

[Instalowanie programu Visual Studio](/visualstudio/install/install-visual-studio)<br/>
[Co nowego w programie Visual Studio](/visualstudio/ide/whats-new-in-visual-studio)<br/>
[Typy projektów C++ w programie Visual Studio](../build/reference/visual-cpp-project-types.md)

::: moniker-end
