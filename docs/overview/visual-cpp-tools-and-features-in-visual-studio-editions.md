---
title: Narzędzia i funkcje programu Visual C++ w wydaniach programu Visual Studio
ms.date: 02/28/2018
helpviewer_keywords:
- versions [C++]
- Visual C++, versions
- editions [C++]
ms.assetid: 3d88607b-9cc4-490a-8d4c-31ee7610a26f
ms.openlocfilehash: a02c4b1d2fc34789993dc782d60246b1af241648
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2019
ms.locfileid: "65222597"
---
# <a name="visual-c-tools-and-features-in-visual-studio-editions"></a>Narzędzia i funkcje programu Visual C++ w wydaniach programu Visual Studio

W poniższych tabelach przedstawiono funkcje języka Visual C++, które są dostępne w programie Visual Studio. Znak X w komórce wskazuje, że funkcja jest dostępna; pusta komórka wskazuje, że funkcja nie jest dostępna. Notatki w nawiasach wskazują, że funkcja jest dostępna, ale jest ograniczona.

## <a name="platforms"></a>Platformy

||||||
|-|-|-|-|-|
|Platforma|Visual Studio Express for Windows 10|Visual Studio Express for Windows Desktop|Visual Studio Community/Professional|Visual Studio Enterprise|
|Windows Desktop||X|X|X|
|Platforma uniwersalna Windows ((telefon, tablet, PC, konsoli Xbox, IoT i HoloLens))|X||X|X|
|Microsoft Store 8.1|||X|X|
|Windows Phone 8.0|||X|X|
|Android|||X|X|
|iOS|||X|X|

## <a name="compilers"></a>Kompilatory

|Kompilator|Visual Studio Express for Windows|Visual Studio Express for Windows Desktop|Visual Studio Professional / Community|Visual Studio Enterprise|
|--------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|X86 32-bitowy kompilator|X|X|X|X|
|X86_arm kompilator krzyżowy|X||X|X|
|x64 64-bitowego kompilatora|||X|X|
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
|OpenMP|X|X|X|X|

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
[SQL Server Data Tools](https://msdn.microsoft.com/library/hh272686)<br/>
