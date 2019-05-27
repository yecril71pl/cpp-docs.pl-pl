---
title: C++Narzędzia i funkcje w wersji programu Visual Studio
ms.date: 05/21/2019
helpviewer_keywords:
- tools and platforms [C++]
ms.assetid: 3d88607b-9cc4-490a-8d4c-31ee7610a26f
ms.openlocfilehash: c5c0459888f8787fd8abba495395130d64a193e0
ms.sourcegitcommit: bde3279f70432f819018df74923a8bb895636f81
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/23/2019
ms.locfileid: "66174778"
---
# <a name="c-tools-and-features-in-visual-studio-editions"></a>C++Narzędzia i funkcje w wersji programu Visual Studio


::: moniker range=">=vs-2019"


Następujące C++ funkcje są dostępne w programie Visual Studio 2019 r. O ile nie wskazano inaczej, wszystkie funkcje są dostępne we wszystkich wersjach: Visual Studio Community, Visual Studio Professional i Visual Studio Enterprise. Niektóre funkcje wymagają konkretnych obciążeń lub składników opcjonalnych, które można zainstalować za pomocą Instalatora programu Visual Studio.

## <a name="platforms"></a>Platformy

- Windows Desktop
- Platforma uniwersalna Windows ((tablet PC, konsoli Xbox, IoT i HoloLens))
- Linux
- Android
- iOS

## <a name="compilers"></a>Kompilatory

- 32-bitowy kompilator MSVC x86 x 64, ARM i ARM64
- 64-bitowy kompilator MSVC x86 x 64, ARM i ARM64
- GCC kompilator krzyżowy dla ARM
- Clang/LLVM
  - W Windows, Clang/LLVM 7.0, x86 lub x64 (tylko Obsługa CMake). Inne wersje Clang może działać, ale oficjalnie nie są obsługiwane.
  - W systemie Linux żadnej instalacji Clang/LLVM obsługiwane przez dystrybucji.
 
## <a name="c-workloads"></a>C++Obciążenia

Program Visual Studio obejmuje następujące obciążenia dla C++ rozwoju. Możesz zainstalować dowolne lub wszystkie z nich, oraz innych obciążeń, takich jak programowanie aplikacji klasycznych .NET, Programowanie w języku Python, programowanie na platformie Azure, programowanie rozszerzeń programu Visual Studio i innych.

### <a name="desktop-development-with-c"></a>Programowanie aplikacji klasycznych w języku C++

Zawartość:
- C++podstawowe funkcje języka

Składniki opcjonalne:
- V142 MSVC - VS 2019 C++ x64/x86 narzędzia build tools (v14.21)
- System Windows 10 SDK (10.0.17763.0)
- Debuger Just In Time
- Narzędzia profilowania dla języka C++
- Narzędzia C++ CMake dla Windows
- C++ ATL dla narzędzia do kompilacji v142 (x86 & x64)
- Rozszerzenia test Adapter for Boost.Test
- Test Adapter for Google Test
- Live Share
- IntelliCode
- IntelliTrace (tylko wersja Enterprise)
- C++ MFC dla narzędzia do kompilacji v142 (x86 & x64)
- C++/ Obsługę interfejsu wiersza polecenia dla narzędzia do kompilacji v142 (14.21)
- Moduły języka C++ dla v142 narzędzia build tools (x64/x86 — wersja eksperymentalna)
- Kompilator clang dla Windows
- IncrediBuild — przyspieszanie kompilacji
- System Windows 10 SDK (10.0.17134.0)
- System Windows 10 SDK (10.0.16299.0)
- Wersji 141 MSVC — premiera programu VS 2017 C++ x64/x86 narzędzia build tools (v14.16)
- W wersji 140 MSVC — VS 2015 C++ narzędzia build tools (14.00)

### <a name="linux-development-with-c"></a>Programowanie dla systemu Linux przy użyciu języka C++

Zawartość:
- Podstawowe funkcje C++
- Windows Universal C Runtime
- Programowanie dla systemu Linux w języku C++

Składniki opcjonalne:
- Narzędzia C++ CMake dla systemu Linux
- Osadzone i narzędzia programistyczne IoT

### <a name="universal-windows-platform-development"></a>Opracowywanie zawartości dla platformy Windows Universal

Zawartość:
- Blend for Visual Studio
- Architektura .NET native i .NET Standard
- Menedżer pakietów NuGet
- Narzędzia platformy Windows uniwersalnej
- System Windows 10 SDK (10.0.17763.0)

Składniki opcjonalne:
- IntelliCode
- IntelliTrace (tylko wersja Enterprise)
- Połączenie urządzenia USB
- Narzędzia platformy uniwersalnej Windows C++ (v142)
- Narzędzia platformy uniwersalnej Windows C++ (w wersji 141)
- Debuger grafiki i profiler procesora GPU dla technologii DirectX
- Windows 10 SDK (10.0.18362.0)
- System Windows 10 SDK (10.0.17134.0)
- System Windows 10 SDK (10.0.16299.0)
- Narzędzia architektury i analizy

### <a name="c-game-development"></a>C++Projektowanie gier

Zawartość:
- Podstawowe funkcje C++
- Windows Universal C Runtime
- Pakiet redystrybucyjny Update C++ 2019
- V142 MSVC - VS 2019 C++ x64/x86 narzędzia build tools (v14.21)

Składniki opcjonalne:
- Narzędzia profilowania dla języka C++
- System Windows 10 SDK (10.0.17763.0)
- IntelliCode
- IntelliTrace (tylko wersja Enterprise)
- System Windows 10 SDK (10.0.17134.0)
- System Windows 10 SDK (10.0.16299.0)
- IncrediBuild — przyspieszanie kompilacji
- Cocos
- Instalator aparatu unreal Engine
- Obsługa systemu android środowisko IDE dla aparatu Unreal engine

### <a name="mobile-development-with-c"></a>Tworzenie aplikacji mobilnych w języku C++

Zawartość:
- Podstawowe funkcje C++
- Instalacja zestawu android SDK (poziom interfejsu API 25) (lokalna instalacja na potrzeby opracowywania aplikacji mobilnych przy użyciu języka C++)

Składniki opcjonalne:
- Android NDK (R16B)
- Apache Ant (1.9.3)
- Narzędzia programistyczne C++ Android
- IntelliCode
- Emulator systemu Google Android (interfejs API poziom 25) (instalacja lokalna)
- Intel Hardware Accelerated Execution Menedżera (HAXM) (instalacja lokalna)
- Android NDK (R16B) (32bit)
- Narzędzia programistyczne dla systemu iOS C++
- IncrediBuild — przyspieszanie kompilacji


## <a name="individual-components"></a>Poszczególne składniki

Te składniki można zainstalować niezależnie od dowolnego obciążenia.

- Diagnostyka JavaScript
- Live Share
- Środowisko wykonawcze C++ Universal Windows Platform, dla narzędzia do kompilacji v142
- Publikowania ClickOnce
- Projekty Instalatora programu Microsoft Visual Studio

## <a name="libraries-and-headers"></a>Nagłówki i biblioteki

- Windows nagłówki i biblioteki
- Windows Universal C Runtime (CRT)
- Standardowa biblioteka C++
- ATL
- MFC
- Biblioteka klas programu .NET Framework
- Biblioteka obsługi języka C++ dla platformy .NET
- OpenMP 2.0
- Ponad 900 bibliotek typu open source za pośrednictwem katalogu vcpkg

## <a name="build-and-project-systems"></a>Skompiluj i zaprojektuj systemy

- CMake
- Dowolny kompilacji systemu za pośrednictwem otwartego folderu
- Kompilacje z wiersza polecenia (msbuild.exe)
- Natywna wielowersyjność
- Z zarządzaną Wielowersyjnością kodu
- Kompilacje równoległe
- Dostosowywanie kompilacji
- Właściwość strony rozszerzalności

## <a name="project-templates"></a>Project Templates

Następujące szablony projektów są dostępne w zależności od obciążeń, które zostały zainstalowane.

Pulpit Windows:
- Pusty projekt
- Aplikacja konsolowa
- Kreator aplikacji klasycznej Windows
- Windows aplikacji klasycznych
- Projekt elementów udostępnionych
- Aplikacja MFC
- Biblioteka dołączana dynamicznie
- Pusty projekt CLR
- Aplikacja konsoli CLR
- Biblioteka statyczna
- Projekt CMake
- Projekt ATL
- Biblioteka dołączana dynamicznie z MFC
- Biblioteka klas CLR
- Projekt pliku reguł programu make (Windows)
- MFC ActiveXControl
- Native Unit Test Project
- Google Test

Universal Windows Platform (C++/CX):
- Pusta aplikacja
- DirectX 11 i XAML aplikacji
- Aplikacja DirectX 11
- DirectX 12 App 
- Aplikacja testów jednostkowych 
- DLL 
- Składnik środowiska wykonawczego systemu Windows 
- Biblioteka statyczna 
- Projekt pakietu aplikacji Windows

W systemie Linux:
- Aplikacja konsoli (Linux)
- Pusty projekt (Linux)
- Urządzenie raspberry Pi Blink
- Projekt pliku reguł programu make (Linux)

## <a name="tools"></a>Narzędzia

- Program łączący (Link.exe)
- Narzędzie Microsoft pliku reguł programu make (Nmake.exe)
- Generator lib (Lib.exe)
- Kompilatora zasobów systemu Windows (Rc.exe)
- Zasób Windows konwertera obiektów (CvtRes.exe)
- Przeglądanie informacji o narzędzie do konserwacji (BscMake.exe)
- Nazwa języka C++ Undecorator (Undname.exe)
- Zrzutu COFF/PE (Dumpbin.exe)
- Edytor COFF/PE (Editbin.exe)
- MASM (Ml.exe)
- Spy++
- ErrLook
- AtlTrace
- Zasady wnioskowania
- Optymalizacja Profilowa

## <a name="debugging-features"></a>Funkcje debugowania

- Debugowanie w trybie macierzystym
- natvis (wizualizacji typem natywnym)
- Debugowanie grafiki
- Zarządzanie debugowaniem
- Użycie procesora GPU
- Użycie pamięci
- Debugowanie zdalne
- Debugowanie SQL
- Statyczna analiza kodu

## <a name="designers-and-editors"></a>Projektanci i edytory

- XAML Designer
- Projektant/Edytor stylów CSS
- Projektant/edytor HTML
- Edytor XML
- Edytor kodu źródłowego
- Funkcje wydajności: Refaktoryzacja, aparat IntelliSense agenci EDG C++ formatowanie kodu
- Projektant Windows Forms
- Projektant danych
- Edytor zasobów natywnych (plików .rc)
- Edytory zasobów
- Edytor modelu
- Projektant cieniowania
- Walidacja aktywnych zależności (tylko wersja Enterprise)
- Architektoniczne diagramy warstwowe (tylko wersja Enterprise)
- Sprawdzanie poprawności architektury (tylko wersja Enterprise)
- Klonowanie kodu (tylko wersja Enterprise)

## <a name="data-features"></a>Funkcje związane z danymi

- Projektant danych
- Obiekty danych
- Usługi sieci Web
- Server Explorer

## <a name="automation-and-extensibility"></a>Automatyzacja i rozszerzalność

- Modele obiektów rozszerzalności
- Model kodu
- Model projektu
- Model edytora zasobów
- Model Kreatora
- Model obiektu debugera

## <a name="application-lifecycle-management-tools"></a>Narzędzia do zarządzania cyklem życia aplikacji

- Testy jednostkowe (kodu natywnego firmy Microsoft C++, Boost.Test, platformy Google Test, narzędzia CTest)
- Kod wykresy mapy i zależności (Professional i Enterprise)
- Pokrycie kodu (tylko Enterprise)
- Ręczne testowanie (tylko wersja Enterprise)
- (Tylko wersja Enterprise) testowania Eksploracyjnego
- Zarządzanie przypadkami testowymi (tylko wersja Enterprise)
- Integracja mapy kodu z debugerem (tylko wersja Enterprise)
- Live Unit Testing (tylko wersja Enterprise)
- IntelliTrace (tylko wersja Enterprise)
- Funkcja IntelliTest (tylko wersja Enterprise)
- Microsoft Fakes (izolacja testu jednostki) (tylko wersja Enterprise)
- Pokrycie kodu (tylko wersja Enterprise)

## <a name="see-also"></a>Zobacz także

[Instalowanie programu Visual Studio](/visualstudio/install/install-visual-studio)<br/>
[Co nowego w programie Visual Studio](/visualstudio/ide/whats-new-in-visual-studio)<br/>
[C++typy projektów w programie Visual Studio](../build/reference/visual-cpp-project-types.md)<br/>

::: moniker-end

::: moniker range="<=vs-2017"

W poniższych tabelach przedstawiono Visual C++ funkcje, które są dostępne w programie Visual Studio 2017. Znak X w komórce wskazuje, że funkcja jest dostępna; pusta komórka wskazuje, że funkcja nie jest dostępna. Notatki w nawiasach wskazują, że funkcja jest dostępna, ale jest ograniczona.

## <a name="platforms"></a>Platformy

||||||
|-|-|-|-|-|
|Platforma|Visual Studio Express for Windows 10|Visual Studio Express for Windows Desktop|Visual Studio Community/Professional|Visual Studio Enterprise|
|Windows Desktop||X|X|X|
|Platforma uniwersalna Windows ((telefon, tablet, PC, konsoli Xbox, IoT i HoloLens))|X||X|X|
|Linux|X|X|
|Microsoft Store 8.1|||X|X|
|Windows Phone 8.0|||X|X|
|Android|||X|X|
|iOS|||X|X|

## <a name="compilers"></a>Kompilatory

|Kompilator|Visual Studio Express for Windows|Visual Studio Express for Windows Desktop|Visual Studio Professional / Community|Visual Studio Enterprise|
|--------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|MSVC X86 32-bitowy kompilator|X|X|X|X|
|X86_arm kompilator krzyżowy|X||X|X|
|MSVC x64 64-bitowego kompilatora|||X|X|
|X86_ x64 cross-compiler|X|X|X|X|

## <a name="libraries-and-headers"></a>Nagłówki i biblioteki

|Biblioteka lub nagłówek|Visual Studio Express for Windows|Visual Studio Express for Windows Desktop|Visual Studio Professional / Community|Visual Studio Enterprise|
|-----------------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|Windows nagłówki i biblioteki i biblioteki CRT|(X)|X|X|X|
|Standardowa biblioteka C++|X|X|X|X|
|ATL|||X|X|
|MFC|||X|X|
|Biblioteka klas programu .NET Framework||X|X|X|
|Biblioteka obsługi języka C++ dla platformy .NET||X|X|X|
|OpenMP 2.0|X|X|X|X|

## <a name="project-templates"></a>Project Templates

|Szablon|Visual Studio Express for Windows|Visual Studio Express for Windows Desktop|Visual Studio Professional / Community|Visual Studio Enterprise|
|--------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|Szablony XAML dla platformy uniwersalnej systemu Windows, Windows 8.1, Windows Phone 8.0|X||X|X|
|Aplikacja Direct3D|X||X|X|
|Biblioteka DLL (Universal Windows)|X||X|X|
|Biblioteka statyczna (Windows Universal)|X||X|X|
|Składnik środowiska wykonawczego systemu Windows|X||X|X|
|Aplikacja testów jednostkowych (Windows Universal)|X||X|X|
|Projekt ATL|||X|X|
|Biblioteka klas (CLR)||X|X|X|
|Aplikacja konsoli CLR||X|X|X|
|Pusty projekt CLR||X|X|X|
|Kreator niestandardowy|||X|X|
|Pusty projekt||X|X|X|
|Projekt pliku reguł programu make||X|X|X|
|Kontrolki ActiveX MFC|||X|X|
|Aplikacja MFC|||X|X|
|MFC DLL|||X|X|
|Projekt testowy|X|X|X|X|
|Aplikacja konsoli Win32||X|X|X|
|Win32 Project||X|X|X|

## <a name="tools"></a>Narzędzia

|Narzędzie|Visual Studio Express for Windows|Visual Studio Express for Windows Desktop|Visual Studio Professional / Community|Visual Studio Enterprise|
|----------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|Program łączący (Link.exe)|X|X|X|X|
|Narzędzie konserwacji programu (Nmake.exe)||X|X|X|
|Generator lib (Lib.exe)|X|X|X|X|
|Kompilatora zasobów systemu Windows (Rc.exe)|X|X|X|X|
|Zasób Windows konwertera obiektów (CvtRes.exe)||X|X|X|
|Przeglądanie informacji o narzędzie do konserwacji (BscMake.exe)|X|X|X|X|
|Nazwa języka C++ Undecorator (Undname.exe)|X|X|X|X|
|Zrzutu COFF/PE (Dumpbin.exe)|X|X|X|X|
|Edytor COFF/PE (Editbin.exe)|X|X|X|X|
|MASM (Ml.exe)|||X|X|
|Spy++|||X|X|
|ErrLook|||X|X|
|AtlTrace|||X|X|
|Devenv.com|||X|X|
|Zasady wnioskowania|||X|X|
|Uaktualnienie programu vcbuild .vcproj do programu MSBuild (VCUpgrade.exe)|X|X|X|X|
|Optymalizacja Profilowa|||X|X|

## <a name="debugging-features"></a>Funkcje debugowania

|Funkcja debugowania|Visual Studio Express for Windows|Visual Studio Express for Windows Desktop|Visual Studio Professional / Community|Visual Studio Enterprise|
|-----------------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|Debugowanie w trybie macierzystym|X|X|X|X|
|natvis (wizualizacji typem natywnym)|X|X|X|X|
|Debugowanie grafiki|X||X|X|
|Zarządzanie debugowaniem||X|X|X|
|Użycie procesora GPU|X||X|X|
|Użycie pamięci|X||X|X|
|Debugowanie zdalne|X|X|X|X|
|Debugowanie SQL|||X|X|
|Statyczna analiza kodu|Ograniczone|Ograniczone|X|X|

## <a name="designers-and-editors"></a>Projektanci i edytory

|Projektant lub Edytor|Visual Studio Express for Windows|Visual Studio Express for Windows Desktop|Visual Studio Professional / Community|Visual Studio Enterprise|
|------------------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|XAML Designer|X||X|X|
|Projektant/Edytor stylów CSS|X|X|X|X|
|Projektant/edytor HTML|X|X|X|X|
|Edytor XML|X|X|X|X|
|Edytor kodu źródłowego|X|X|X|X|
|Funkcje wydajności: Refaktoryzacja, funkcja IntelliSense, formatowania kodu C++|X|X|X|X|
|Projektant Windows Forms||X|X|X|
|Projektant danych|||X|X|
|Edytor zasobów natywnych (plików .rc)|||X|X|
|Edytory zasobów|X|X|X|X|
|Edytor modelu|X||X|X|
|Projektant cieniowania|X||X|X|

## <a name="data-features"></a>Funkcje związane z danymi

|Funkcja danych|Visual Studio Express for Windows|Visual Studio Express for Windows Desktop|Visual Studio Professional / Community|Visual Studio Enterprise|
|------------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|Projektant danych|||X|X|
|Obiekty danych|||X|X|
|Usługi sieci Web|||X|X|
|Server Explorer|||X|X|

## <a name="build-and-project-systems"></a>Skompiluj i zaprojektuj systemy

|Kompilacja lub funkcja projektu|Visual Studio Express for Windows|Visual Studio Express for Windows Desktop|Visual Studio Professional / Community|Visual Studio Enterprise|
|------------------------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|Kompilacje z wiersza polecenia (msbuild.exe)|X|X|X|X|
|Natywna wielowersyjność||X|X|X|
|Z zarządzaną Wielowersyjnością kodu||X|X|X|
|Kompilacje równoległe|X|X|X|X|
|Dostosowywanie kompilacji|X|X|X|X|
|Właściwość strony rozszerzalności|X|X|X|X|

## <a name="automation-and-extensibility"></a>Automatyzacja i rozszerzalność

|Automatyzacja i rozszerzalność|Visual Studio Express for Windows|Visual Studio Express for Windows Desktop|Visual Studio Professional / Community|Visual Studio Enterprise|
|----------------------------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|Modele obiektów rozszerzalności|||X|X|
|Model kodu|||X|X|
|Model projektu|||X|X|
|Model edytora zasobów|||X|X|
|Model Kreatora|||X|X|
|Model obiektu debugera|||X|X|

## <a name="application-lifecycle-management-tools"></a>Narzędzia do zarządzania cyklem życia aplikacji

||||||
|-|-|-|-|-|
|Narzędzie|Visual Studio Express for Windows|Visual Studio Express for Windows Desktop|Visual Studio Professional / Community|Visual Studio Enterprise|
|Unit Testing (natywnej struktury)|X|X|X|X|
|Unit Testing (zarządzane framework)||X|X|X|
|Pokrycie kodu||||X|
|Testowanie ręczne||||X|
|Testowanie eksploracyjne||||X|
|Zarządzanie przypadkami testowymi||||X|
|Wykresy mapy i zależności kodu|||tylko do odczytu|X|
|Debugowanie mapy kodów||||X|

## <a name="see-also"></a>Zobacz także

[Instalowanie programu Visual Studio](/visualstudio/install/install-visual-studio)<br/>
[Co nowego w programie Visual Studio](/visualstudio/ide/whats-new-in-visual-studio)<br/>
[C++typy projektów w programie Visual Studio](../build/reference/visual-cpp-project-types.md)<br/>

::: moniker-end
