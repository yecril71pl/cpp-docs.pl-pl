---
title: "Narzędzia Visual C++ i funkcji w wersjach programu Visual Studio | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- versions [C++]
- Visual C++, versions
- editions [C++]
ms.assetid: 3d88607b-9cc4-490a-8d4c-31ee7610a26f
caps.latest.revision: "51"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 37f1eed2287c8fe655a124b1f76f48a203ab1607
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="visual-c-tools-and-features-in-visual-studio-editions"></a>Narzędzia Visual C++ i funkcji w wersjach programu Visual Studio
W poniższej tabeli przedstawiono funkcje programu Visual C++, które są dostępne w programie Visual Studio. X w komórce oznacza, że funkcja jest dostępna; pusta komórka wskazuje, że funkcja nie jest dostępna. Uwagi w nawiasach wskazują, że funkcja jest dostępne, ale ograniczone.  
  
## <a name="platforms"></a>Platformy  
  
||||||  
|-|-|-|-|-|  
|Platforma|Visual Studio Express for Windows 10|Visual Studio Express for Windows Desktop|Visual Studio Community/Professional|Visual Studio Enterprise|  
|System Windows Desktop||X|X|X|  
|Platforma uniwersalna systemu Windows ((telefonów, tabletu PC, Xbox, IoT i HoloLens))|X||X|X|  
|Sklep Windows 8.1|||X|X|  
|Windows Phone 8.0|||X|X|  
|Android|||X|X|  
|iOS|||X|X|  
  
## <a name="compilers"></a>Kompilatory  
  
|Kompilatora|Visual Studio Express dla systemu Windows|Visual Studio Express for Windows Desktop|Visual Studio Professional / Community|Visual Studio Enterprise|  
|--------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|  
|32-bitowych X86 kompilatora|X|X|X|X|  
|X86_arm cross kompilatora|X||X|X|  
|64-bitowych [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] kompilatora|||X|X|  
|X86_ [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] między kompilatora|X|X|X|X|  
  
## <a name="libraries-and-headers"></a>Nagłówki i biblioteki  
  
|Biblioteki lub nagłówka|Visual Studio Express dla systemu Windows|Visual Studio Express for Windows Desktop|Visual Studio Professional / Community|Visual Studio Enterprise|  
|-----------------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|  
|Windows nagłówki i biblioteki i Biblioteka CRT|(X)|X|X|X|  
|Standardowa biblioteka C++|X|X|X|X|  
|ATL|||X|X|  
|MFC|||X|X|  
|Biblioteka klas programu .NET Framework||X|X|X|  
|Biblioteka obsługi języka C++ dla platformy .NET||X|X|X|  
|OpenMP|X|X|X|X|  
  
## <a name="project-templates"></a>Szablony projektu  
  
|Szablon|Visual Studio Express dla systemu Windows|Visual Studio Express for Windows Desktop|Visual Studio Professional / Community|Visual Studio Enterprise|  
|--------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|  
|Szablony XAML dla platformy uniwersalnej systemu Windows, Windows 8.1, Windows Phone 8.0|X||X|X|  
|Aplikacja Direct3D|X||X|X|  
|DLL (aplikacje do Sklepu Windows)|X||X|X|  
|Biblioteka statyczna (aplikacje do Sklepu Windows)|X||X|X|  
|Składnik środowiska wykonawczego systemu Windows|X||X|X|  
|Biblioteka testów jednostki (aplikacje do Sklepu Windows)|X||X|X|  
|Projekt ATL|||X|X|  
|Biblioteka klas (CLR)||X|X|X|  
|Aplikacja konsoli środowiska CLR||X|X|X|  
|Pusty projekt CLR||X|X|X|  
|Kreator niestandardowy|||X|X|  
|Pusty projekt||X|X|X|  
|Projektu pliku reguł programu make||X|X|X|  
|Kontrolki ActiveX MFC|||X|X|  
|Aplikacji MFC|||X|X|  
|BIBLIOTEKI MFC DLL|||X|X|  
|Projekt testowy|X|X|X|X|  
|Aplikacji konsoli Win32||X|X|X|  
|Projekt Win32||X|X|X|  
  
## <a name="tools"></a>Narzędzia  
  
|Narzędzie|Visual Studio Express dla systemu Windows|Visual Studio Express for Windows Desktop|Visual Studio Professional / Community|Visual Studio Enterprise|  
|----------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|  
|Konsolidatora przyrostowego (Link.exe)|X|X|X|X|  
|Narzędzie konserwacji programu (Nmake.exe)||X|X|X|  
|Generator lib (Lib.exe)|X|X|X|X|  
|Kompilator zasobów systemu Windows (Rc.exe)|X|X|X|X|  
|Zasób systemu Windows, aby obiekt konwertera (CvtRes.exe)||X|X|X|  
|Przeglądanie informacji narzędzie do konserwacji (BscMake.exe)|X|X|X|X|  
|Nazwa języka C++ Undecorator (Undname.exe)|X|X|X|X|  
|COFF/PE zrzutu (Dumpbin.exe)|X|X|X|X|  
|Edytor COFF/PE (Editbin.exe)|X|X|X|X|  
|MASM (Ml.exe)|||X|X|  
|Spy++|||X|X|  
|ErrLook|||X|X|  
|AtlTrace|||X|X|  
|Devenv.com|||X|X|  
|Zasady wnioskowania|||X|X|  
|Uaktualnij program VCBuild .vcproj projektów dla programu MSBuild (VCUpgrade.exe)|X|X|X|X|  
|Optymalizacja sterowana profilem|||X|X|  
  
## <a name="debugging-features"></a>Funkcje debugowania  
  
|Funkcja debugowania|Visual Studio Express dla systemu Windows|Visual Studio Express for Windows Desktop|Visual Studio Professional / Community|Visual Studio Enterprise|  
|-----------------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|  
|Debugowanie w trybie macierzystym|X|X|X|X|  
|natvis (natywny typ wizualizacji)|X|X|X|X|  
|Debugowanie grafiki|X||X|X|  
|Debugowania zarządzanego||X|X|X|  
|Użycie procesora GPU|X||X|X|  
|Użycie pamięci|X||X|X|  
|Debugowanie zdalne|X|X|X|X|  
|Debugowanie SQL|||X|X|  
|Statycznej analizy kodu|Ograniczone|Ograniczone|X|X|  
  
## <a name="designers-and-editors"></a>Projektanci i edytory  
  
|Projektancie lub edytorze|Visual Studio Express dla systemu Windows|Visual Studio Express for Windows Desktop|Visual Studio Professional / Community|Visual Studio Enterprise|  
|------------------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|  
|XAML Designer|X||X|X|  
|Edytor projektanta stylów CSS|X|X|X|X|  
|Edytor projektanta HTML|X|X|X|X|  
|Edytor XML|X|X|X|X|  
|Edytor kodu źródłowego|X|X|X|X|  
|Funkcje produktywności: Refaktoryzacji IntelliSense, formatowania kodu C++|X|X|X|X|  
|Projektant Windows Forms||X|X|X|  
|Projektant danych|||X|X|  
|Edytor zasobów Native (.RC — pliki)|||X|X|  
|Edytory zasobów|X|X|X|X|  
|Edytor modelu|X||X|X|  
|Projektant programu do cieniowania|X||X|X|  
  
## <a name="data-features"></a>Funkcje związane z danymi  
  
|Funkcja danych|Visual Studio Express dla systemu Windows|Visual Studio Express for Windows Desktop|Visual Studio Professional / Community|Visual Studio Premium|Visual Studio Enterprise|  
|------------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|---------------------------|------------------------------|  
|Projektant danych|||X|X|X|  
|Obiekty danych|||X|X|X|  
|Usługi sieci Web|||X|X|X|  
|Server Explorer|||X|X|X|  
  
## <a name="build-and-project-systems"></a>Kompilowanie i systemów projektów  
  
|Kompilacji lub funkcji projektu|Visual Studio Express dla systemu Windows|Visual Studio Express for Windows Desktop|Visual Studio Professional / Community|Visual Studio Enterprise|  
|------------------------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|  
|Kompilacji wiersza polecenia (msbuild.exe)|X|X|X|X|  
|Natywny Wielowersyjność kodu||X|X|X|  
|Zarządzane Wielowersyjność kodu||X|X|X|  
|Równoległych kompilacji|X|X|X|X|  
|Dostosowania kompilacji|X|X|X|X|  
|Rozszerzalność strony właściwości|X|X|X|X|  
  
## <a name="automation-and-extensibility"></a>Automatyzacja i rozszerzalność  
  
|Automatyzacja i rozszerzalność|Visual Studio Express dla systemu Windows|Visual Studio Express for Windows Desktop|Visual Studio Professional / Community|Visual Studio Enterprise|  
|----------------------------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|  
|Modele obiektowe rozszerzalności|||X|X|  
|Model kodu|||X|X|  
|Model projektu|||X|X|  
|Edytor zasobów modelu|||X|X|  
|Kreator modelu|||X|X|  
|Model obiektów debugera|||X|X|  
  
## <a name="application-lifecycle-management-tools"></a>Narzędzia do zarządzania cyklem życia aplikacji  
  
||||||  
|-|-|-|-|-|  
|Narzędzie|Visual Studio Express dla systemu Windows|Visual Studio Express for Windows Desktop|Visual Studio Professional / Community|Visual Studio Enterprise|  
|Testowanie jednostkowe (native framework)|X|X|X|X|  
|Testowanie jednostkowe (zarządzane struktury)||X|X|X|  
|Pokrycie kodu||||X|  
|Testów ręcznych||||X|  
|Testowanie eksploracyjne||||X|  
|Zarządzanie przypadkami testowymi||||X|  
|Kod wykresy mapy i zależności|||tylko do odczytu|X|  
|Kod debugowania mapy||||X|  
  
## <a name="see-also"></a>Zobacz też  
 [Zainstaluj program Visual Studio](/visualstudio/install/install-visual-studio)   
 [Co to jest nowe w programie Visual Studio](/visualstudio/ide/whats-new-in-visual-studio)   
 [Typy projektów Visual C++](../ide/visual-cpp-project-types.md)   
 [Wersje narzędzia graficzne bazy danych](http://msdn.microsoft.com/en-us/a7689adc-f16b-4cc7-b6fe-39ca0c711161)