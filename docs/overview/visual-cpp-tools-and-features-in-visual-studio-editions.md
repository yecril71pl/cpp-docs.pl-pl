---
title: Narzędzia i funkcje języka C++ w wersjach programu Visual Studio
ms.date: 05/21/2019
helpviewer_keywords:
- tools and platforms [C++]
ms.assetid: 3d88607b-9cc4-490a-8d4c-31ee7610a26f
ms.openlocfilehash: 88eb66440df023254cb806c03a00aa2d71980305
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366798"
---
# <a name="c-tools-and-features-in-visual-studio-editions"></a>Narzędzia i funkcje języka C++ w wersjach programu Visual Studio

::: moniker range=">=vs-2019"

Następujące funkcje języka C++ są dostępne w programie Visual Studio 2019. O ile nie określono inaczej, wszystkie funkcje są dostępne we wszystkich wersjach: Visual Studio Community, Visual Studio Professional i Visual Studio Enterprise. Niektóre funkcje wymagają określonych obciążeń lub składników opcjonalnych, które można zainstalować za pomocą Instalatora programu Visual Studio.

## <a name="platforms"></a>Platformy

- Pulpit systemu Windows
- Uniwersalna platforma Systemu Windows ((tablet, PC, Xbox, IoT i HoloLens))
- Linux
- Android
- iOS

## <a name="compilers"></a>Kompilatory

- Kompilator 32-bitowy MSVC dla x86, x64, ARM i ARM64
- Kompilator 64-bitowy MSVC dla x86, x64, ARM i ARM64
- Kompilator krzyżowy GCC dla ARM
- Clang/LLVM
  - W systemie Windows, Clang/LLVM 7.0, kierowanie x86 lub x64 (CMake tylko wsparcie). Inne wersje Clang mogą działać, ale nie są oficjalnie obsługiwane.
  - W systemie Linux każda instalacja Clang/LLVM obsługiwana przez dystrybucję.

## <a name="c-workloads"></a>Obciążenia języka C++

Visual Studio zawiera następujące obciążenia dla rozwoju języka C++. Można zainstalować dowolne lub wszystkie z nich, wraz z innymi obciążeniami, takimi jak .NET Desktop Development, Rozwój języka Python, program azure development, program visual studio extension development i inne.

### <a name="desktop-development-with-c"></a>Programowanie aplikacji klasycznych w języku C++

Zawarte:

- Funkcje pulpitu w języku C++

Opcjonalne komponenty:

- MSVC v142 - VS 2019 C++ x64/x86 narzędzia kompilacji (wersja 14.21)
- Windows 10 SDK (10.0.17763.0)
- Debuger just-in-time
- Narzędzia profilowania języka C++
- C++ CMake narzędzia dla systemu Windows
- C++ ATL dla v142 build tools (x86 & x64)
- Adapter testowy do boost.test
- Adapter testowy do testu Google
- Live Share
- IntelliCode
- IntelliTrace (tylko dla przedsiębiorstw)
- C++ MFC dla v142 build tools (x86 & x64)
- Obsługa C++/CLI dla narzędzi kompilacji w wersji 142 (14.21)
- Moduły C++ dla narzędzi do budowania wersji 142 (x64/x86 – eksperymentalne)
- Kompilator clang dla systemu Windows
- IncrediBuild - Przyspieszenie kompilacji
- Windows 10 SDK (10.0.17134.0)
- Windows 10 SDK (10.0.16299.0)
- MSVC v141 - VS 2017 C++ x64/x86 narzędzia kompilacji (wersja 14.16)
- MSVC v140 — VS 2015 C++ narzędzia kompilacji (wersja 14.00)

### <a name="linux-development-with-c"></a>Programowanie dla systemu Linux w języku C++

Zawarte:

- Podstawowe funkcje języka C++
- Uniwersalny czas pracy systemu Windows C
- C++ dla rozwoju Linuksa

Opcjonalne komponenty:

- C++ CMake narzędzia dla Linuksa
- Wbudowane i IoT narzędzia programistyczne

### <a name="universal-windows-platform-development"></a>Tworzenie uniwersalnej platformy systemu Windows

Zawarte:

- Blend for Visual Studio
- Natywny i .NET Standard platformy .NET
- Menedżer pakietów NuGet
- Narzędzia platformy uniwersalnej systemu Windows
- Windows 10 SDK (10.0.17763.0)

Opcjonalne komponenty:

- IntelliCode
- IntelliTrace (tylko dla przedsiębiorstw)
- Łączność z urządzeniem USB
- Narzędzia uniwersalnej platformy systemu Windows w języku C++ (v142)
- Narzędzia uniwersalnej platformy systemu Windows w języku C++ (v141)
- Debuger grafiki i profiler GPU dla DirectX
- Windows 10 SDK (10.0.18362.0)
- Windows 10 SDK (10.0.17134.0)
- Windows 10 SDK (10.0.16299.0)
- Architektura i narzędzia analityczne

### <a name="c-game-development"></a>Rozwój gier w języku C++

Zawarte:

- Podstawowe funkcje języka C++
- Uniwersalny czas pracy systemu Windows C
- Aktualizacja redystrybucjowa C++ 2019
- MSVC v142 - VS 2019 C++ x64/x86 narzędzia kompilacji (wersja 14.21)

Opcjonalne komponenty:

- Narzędzia profilowania języka C++
- Windows 10 SDK (10.0.17763.0)
- IntelliCode
- IntelliTrace (tylko dla przedsiębiorstw)
- Windows 10 SDK (10.0.17134.0)
- Windows 10 SDK (10.0.16299.0)
- IncrediBuild - Przyspieszenie kompilacji
- Cocos
- Instalator Unreal Engine
- Obsługa środowiska Android IDE dla silnika Unreal

### <a name="mobile-development-with-c"></a>Tworzenie aplikacji mobilnych w języku C++

Zawarte:

- Podstawowe funkcje języka C++
- Konfiguracja SDK systemu Android (poziom INTERFEJSU API 25) (instalacja lokalna dla rozwoju urządzeń przenośnych z C++)

Opcjonalne komponenty:

- Android NDK (R16B)
- Mrówka Apache (1.9.3)
- Narzędzia programistyczne dla systemu Android w języku C++
- IntelliCode
- Google Android Emulator (API Poziom 25) (instalacja lokalna)
- Intel Hardware Accelerated Execution Manager (HAXM) (instalacja lokalna)
- Android NDK (R16B) (32-bitowy)
- Narzędzia programistyczne systemu iOS w języku C++
- IncrediBuild - Przyspieszenie kompilacji

## <a name="individual-components"></a>Poszczególne komponenty

Składniki te można zainstalować niezależnie od obciążenia.

- Diagnostyka JavaScript
- Live Share
- Uniwersalny czas pracy platformy systemu Windows W języku C++ dla narzędzi kompilacji w wersji 142
- Kliknij publikowanieonce
- Projekty instalatora programu Microsoft Visual Studio

## <a name="libraries-and-headers"></a>Biblioteki i nagłówki

- Nagłówki i biblioteki systemu Windows
- Uniwersalny czas pracy systemu Windows C (CRT)
- Standardowa biblioteka C++
- ATL
- MFC
- Biblioteka klas programu .NET Framework
- Biblioteka pomocy technicznej języka C++ dla platformy .NET
- OpenMP 2.0
- Ponad 900 bibliotek open source za pośrednictwem katalogu vcpkg

## <a name="build-and-project-systems"></a>Systemy kompilacji i projektów

- CMake
- Dowolny system kompilacji za pośrednictwem folderu Open
- Kompilacje wiersza polecenia (msbuild.exe)
- Natywne kierowanie wielokrotne
- Zarządzane kierowanie zbiorcze
- Kompilacje równoległe
- Konstruuj dostosowania
- Rozszerzalność stron właściwości

## <a name="project-templates"></a>Szablony projektów

Następujące szablony projektów są dostępne w zależności od tego, które obciążenia zostały zainstalowane.

Pulpit systemu Windows:

- Pusty projekt
- Aplikacja konsoli
- Kreator pulpitu systemu Windows
- Aplikacja klasyczna systemu Windows
- Projekt elementów udostępnionych
- Aplikacja MFC
- Biblioteka łączy dynamicznych
- Pusty projekt CLR
- Aplikacja konsoli CLR
- Biblioteka statyczna
- Projekt CMake
- Projekt ATL
- Biblioteka łączy dynamicznych MFC
- Biblioteka klas CLR
- Projekt Makefile (Windows)
- MFC ActiveXControl
- Natywny projekt testu jednostkowego
- Google Test

Uniwersalna platforma Windows (C++/CX):

- Pusta aplikacja
- Aplikacja DirectX 11 i XAML
- Aplikacja DirectX 11
- Aplikacja DirectX 12
- Aplikacja testowa jednostki
- DLL
- Składnik środowiska wykonawczego systemu Windows
- Biblioteka statyczna
- Projekt pakietu aplikacji systemu Windows

W systemie Linux:

- Aplikacja konsoli (Linux)
- Pusty projekt (Linux)
- Raspberry Pi Miga
- Projekt Makefile (Linux)

## <a name="tools"></a>Narzędzia

- Łącznik przyrostowy (Link.exe)
- Narzędzie Microsoft Makefile (Nmake.exe)
- Lib Generator (Lib.exe)
- Kompilator zasobów systemu Windows (rc.exe)
- Konwerter zasobów systemu Windows do obiektów (cvtRes.exe)
- Przeglądaj narzędzie do konserwacji informacji (BscMake.exe)
- C++ Nazwa Undecorator (Undname.exe)
- Wywrotka COFF/PE (Dumpbin.exe)
- Edytor COFF/PE (Editbin.exe)
- MASM (ml.exe)
- Spy++
- Errlook
- AtlTrace (AtlTrace)
- Zasady wnioskowania
- Optymalizacje z przewodnikiem w profilu

## <a name="debugging-features"></a>Funkcje debugowania

- Debugowanie natywne
- natvis (wizualizacja typu macierzystego)
- Debugowanie grafiki
- Debugowanie zarządzane
- Użycie gpu
- Użycie pamięci
- Debugowanie zdalne
- Debugowanie SQL
- Statyczna analiza kodu

## <a name="designers-and-editors"></a>Projektanci i redaktorzy

- XAML Designer
- Projektant/edytor stylu CSS
- Projektant/edytor HTML
- Edytor XML
-  Edytor kodu źródłowego
- Funkcje produktywności: Refaktoryzowanie, silnik EDG IntelliSense, formatowanie kodu C++
- Projektant Windows Forms
- Projektant danych
- Edytor zasobów natywnych (pliki rc)
- Edytory zasobów
- Edytor modelu
- Projektant cieniowania
- Sprawdzanie poprawności zależności na żywo (tylko w przedsiębiorstwie)
- Diagramy warstw architektonicznych (tylko w przedsiębiorstwie)
- Sprawdzanie poprawności architektury (tylko w przedsiębiorstwie)
- Klonowanie kodu (tylko w przedsiębiorstwie)

## <a name="data-features"></a>Funkcje danych

- Projektant danych
- Obiekty danych
- Usługi internetowe
- Eksplorator serwera

## <a name="automation-and-extensibility"></a>Automatyzacja i rozszerzalność

- Modele obiektów rozszerzalności
- Model kodu
- Model projektu
- Model Edytora zasobów
- Model kreatora
- Model obiektu debugera

## <a name="application-lifecycle-management-tools"></a>Narzędzia do zarządzania cyklem życia aplikacji

- Testowanie jednostkowe (Microsoft Native C++, Boost.Test, Test Google, CTest)
- Wykresy mapy kodu i zależności (profesjonalne i korporacyjne)
- Pokrycie kodu (tylko w przedsiębiorstwie)
- Testowanie ręczne (tylko w przedsiębiorstwie)
- Badania rozpoznawcze (tylko w przedsiębiorstwie)
- Zarządzanie przyzdbywami testowymi (tylko w przedsiębiorstwie)
- Integracja debugera mapy kodu (tylko enterprise)
- Testowanie jednostek na żywo (tylko dla przedsiębiorstw)
- IntelliTrace (tylko dla przedsiębiorstw)
- IntelliTest (tylko dla przedsiębiorstw)
- Microsoft Fakes (izolacja testu jednostkowego) (tylko w przedsiębiorstwie)
- Pokrycie kodu (tylko enterprise)

## <a name="see-also"></a>Zobacz też

[Instalowanie programu Visual Studio](/visualstudio/install/install-visual-studio)<br/>
[Co nowego w programie Visual Studio](/visualstudio/ide/whats-new-in-visual-studio)<br/>
[Typy projektów języka C++ w programie Visual Studio](../build/reference/visual-cpp-project-types.md)

::: moniker-end

::: moniker range="<=vs-2017"

W poniższych tabelach przedstawiono funkcje programu Visual C++, które są dostępne w programie Visual Studio 2017. Znak X w komórce wskazuje, że funkcja jest dostępna; pusta komórka wskazuje, że funkcja nie jest dostępna. Notatki w nawiasach wskazują, że funkcja jest dostępna, ale ograniczona.

## <a name="platforms"></a>Platformy

||||||
|-|-|-|-|-|
|Platforma|Visual Studio Express dla systemu Windows 10|Visual Studio Express dla pulpitu systemu Windows|Społeczność programu Visual Studio/Profesjonaliści|Visual Studio Enterprise|
|Pulpit systemu Windows||X|X|X|
|Uniwersalna platforma Windows ((telefon, tablet, komputer, Xbox, IoT i HoloLens))|X||X|X|
|Linux|X|X|
|Sklep Microsoft Store 8.1|||X|X|
|Windows Phone 8.0|||X|X|
|Android|||X|X|
|iOS|||X|X|

## <a name="compilers"></a>Kompilatory

|Kompilator|Visual Studio Express dla systemu Windows|Visual Studio Express dla pulpitu systemu Windows|Visual Studio Professional / Społeczność|Visual Studio Enterprise|
|--------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|32-bitowy kompilator X86 MSVC|X|X|X|X|
|X86_arm kompilator krzyżowy|X||X|X|
|Kompilator 64-bitowy x64 MSVC|||X|X|
|X86_ kompilatora krzyżowego x64|X|X|X|X|

## <a name="libraries-and-headers"></a>Biblioteki i nagłówki

|Biblioteka lub nagłówek|Visual Studio Express dla systemu Windows|Visual Studio Express dla pulpitu systemu Windows|Visual Studio Professional / Społeczność|Visual Studio Enterprise|
|-----------------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|Nagłówki i biblioteki systemu Windows oraz biblioteka CRT|(X)|X|X|X|
|Standardowa biblioteka C++|X|X|X|X|
|ATL|||X|X|
|MFC|||X|X|
|Biblioteka klas programu .NET Framework||X|X|X|
|Biblioteka pomocy technicznej języka C++ dla platformy .NET||X|X|X|
|OpenMP 2.0|X|X|X|X|

## <a name="project-templates"></a>Szablony projektów

|Szablon|Visual Studio Express dla systemu Windows|Visual Studio Express dla pulpitu systemu Windows|Visual Studio Professional / Społeczność|Visual Studio Enterprise|
|--------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|Szablony XAML dla platformy uniwersalnej systemu Windows, Windows 8.1, Windows Phone 8.0|X||X|X|
|Aplikacja Direct3D|X||X|X|
|Biblioteka DLL (uniwersalny system Windows)|X||X|X|
|Biblioteka statyczna (uniwersalny system Windows)|X||X|X|
|Składnik środowiska wykonawczego systemu Windows|X||X|X|
|Aplikacja testowa jednostek (uniwersalny system Windows)|X||X|X|
|Projekt ATL|||X|X|
|Biblioteka klas (CLR)||X|X|X|
|Aplikacja konsoli CLR||X|X|X|
|Pusty projekt CLR||X|X|X|
|Kreator niestandardowy|||X|X|
|Pusty projekt||X|X|X|
|Projekt Makefile||X|X|X|
|Sterowanie MFC ActiveX|||X|X|
|Aplikacja MFC|||X|X|
|MFC DLL|||X|X|
|Projekt testowy|X|X|X|X|
|Aplikacja konsoli Win32||X|X|X|
|Projekt Win32||X|X|X|

## <a name="tools"></a>Narzędzia

|Narzędzie|Visual Studio Express dla systemu Windows|Visual Studio Express dla pulpitu systemu Windows|Visual Studio Professional / Społeczność|Visual Studio Enterprise|
|----------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|Łącznik przyrostowy (Link.exe)|X|X|X|X|
|Narzędzie do konserwacji programu (Nmake.exe)||X|X|X|
|Lib Generator (Lib.exe)|X|X|X|X|
|Kompilator zasobów systemu Windows (rc.exe)|X|X|X|X|
|Konwerter zasobów systemu Windows do obiektów (cvtRes.exe)||X|X|X|
|Przeglądaj narzędzie do konserwacji informacji (BscMake.exe)|X|X|X|X|
|C++ Nazwa Undecorator (Undname.exe)|X|X|X|X|
|Wywrotka COFF/PE (Dumpbin.exe)|X|X|X|X|
|Edytor COFF/PE (Editbin.exe)|X|X|X|X|
|MASM (ml.exe)|||X|X|
|Spy++|||X|X|
|Errlook|||X|X|
|AtlTrace (AtlTrace)|||X|X|
|Devenv.com|||X|X|
|Zasady wnioskowania|||X|X|
|Uaktualnianie projektów VCBuild .vcproj do msbuild (VCUpgrade.exe)|X|X|X|X|
|Optymalizacje z przewodnikiem w profilu|||X|X|

## <a name="debugging-features"></a>Funkcje debugowania

|Funkcja debugowania|Visual Studio Express dla systemu Windows|Visual Studio Express dla pulpitu systemu Windows|Visual Studio Professional / Społeczność|Visual Studio Enterprise|
|-----------------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|Debugowanie natywne|X|X|X|X|
|natvis (wizualizacja typu macierzystego)|X|X|X|X|
|Debugowanie grafiki|X||X|X|
|Debugowanie zarządzane||X|X|X|
|Użycie gpu|X||X|X|
|Użycie pamięci|X||X|X|
|Debugowanie zdalne|X|X|X|X|
|Debugowanie SQL|||X|X|
|Statyczna analiza kodu|Ograniczone|Ograniczone|X|X|

## <a name="designers-and-editors"></a>Projektanci i redaktorzy

|Projektant lub edytor|Visual Studio Express dla systemu Windows|Visual Studio Express dla pulpitu systemu Windows|Visual Studio Professional / Społeczność|Visual Studio Enterprise|
|------------------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|XAML Designer|X||X|X|
|Projektant/edytor stylu CSS|X|X|X|X|
|Projektant/edytor HTML|X|X|X|X|
|Edytor XML|X|X|X|X|
| Edytor kodu źródłowego|X|X|X|X|
|Funkcje produktywności: Refaktoryzowanie, IntelliSense, Formatowanie kodu W++|X|X|X|X|
|Projektant Windows Forms||X|X|X|
|Projektant danych|||X|X|
|Edytor zasobów natywnych (pliki rc)|||X|X|
|Edytory zasobów|X|X|X|X|
|Edytor modelu|X||X|X|
|Projektant cieniowania|X||X|X|

## <a name="data-features"></a>Funkcje danych

|Funkcja danych|Visual Studio Express dla systemu Windows|Visual Studio Express dla pulpitu systemu Windows|Visual Studio Professional / Społeczność|Visual Studio Enterprise|
|------------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|Projektant danych|||X|X|
|Obiekty danych|||X|X|
|Usługi internetowe|||X|X|
|Eksplorator serwera|||X|X|

## <a name="build-and-project-systems"></a>Systemy kompilacji i projektów

|Funkcja kompilacji lub projektu|Visual Studio Express dla systemu Windows|Visual Studio Express dla pulpitu systemu Windows|Visual Studio Professional / Społeczność|Visual Studio Enterprise|
|------------------------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|Kompilacje wiersza polecenia (msbuild.exe)|X|X|X|X|
|Natywne kierowanie wielokrotne||X|X|X|
|Zarządzane kierowanie zbiorcze||X|X|X|
|Kompilacje równoległe|X|X|X|X|
|Konstruuj dostosowania|X|X|X|X|
|Rozszerzalność stron właściwości|X|X|X|X|

## <a name="automation-and-extensibility"></a>Automatyzacja i rozszerzalność

|Automatyzacja i rozszerzalność|Visual Studio Express dla systemu Windows|Visual Studio Express dla pulpitu systemu Windows|Visual Studio Professional / Społeczność|Visual Studio Enterprise|
|----------------------------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|Modele obiektów rozszerzalności|||X|X|
|Model kodu|||X|X|
|Model projektu|||X|X|
|Model Edytora zasobów|||X|X|
|Model kreatora|||X|X|
|Model obiektu debugera|||X|X|

## <a name="application-lifecycle-management-tools"></a>Narzędzia do zarządzania cyklem życia aplikacji

||||||
|-|-|-|-|-|
|Narzędzie|Visual Studio Express dla systemu Windows|Visual Studio Express dla pulpitu systemu Windows|Visual Studio Professional / Społeczność|Visual Studio Enterprise|
|Testowanie jednostkowe (struktura macierzysta)|X|X|X|X|
|Testowanie jednostkowe (struktura zarządzana)||X|X|X|
|Pokrycie kodu||||X|
|Testowanie ręczne||||X|
|Testowanie eksploracyjne||||X|
|Zarządzanie przypadkami testowymi||||X|
|Wykresy mapy kodu i zależności|||tylko do odczytu|X|
|Debugowanie mapy kodu||||X|

## <a name="see-also"></a>Zobacz też

[Instalowanie programu Visual Studio](/visualstudio/install/install-visual-studio)<br/>
[Co nowego w programie Visual Studio](/visualstudio/ide/whats-new-in-visual-studio)<br/>
[Typy projektów języka C++ w programie Visual Studio](../build/reference/visual-cpp-project-types.md)

::: moniker-end
