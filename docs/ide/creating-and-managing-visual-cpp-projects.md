---
title: Tworzenie i zarządzanie projektami Visual C++ | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vcprojects
- creatingmanagingVC
dev_langs:
- C++
helpviewer_keywords:
- ATL projects, creating
- Visual C++ projects, creating
- projects [C++], creating
- Visual C++ projects
- ATL projects
ms.assetid: 11003cd8-9046-4630-a189-a32bf3b88047
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 41b3565893d65990955f0fd28c6cccce7fcb1f32
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43222246"
---
# <a name="creating-and-managing-msbuild-based-visual-c-projects"></a>Tworzenie i zarządzanie projektami opartych na platformie MSBuild Visual C++
Program MSBuild jest system kompilacji natywne w języku Visual C++ i zazwyczaj najlepsze kompilacji systemowi operacyjnemu używanie dla aplikacji platformy uniwersalnej systemu Windows, a także aplikacji pulpitu, które używają biblioteki ATL i MFC. Program MSBuild jest ściśle zintegrowana za pomocą środowiska IDE programu Visual Studio i system projektu, ale można go także użyć w wierszu polecenia. Począwszy od programu Visual Studio 2017, Visual C++ obsługuje [CMake i innych systemów innych niż MSBuild, za pomocą funkcji Otwórz Folder](non-msbuild-projects.md).

Z opartych na platformie MSBuild projekt zawiera plik projektu w formacie XML (.vcxproj), która określa wszystkie pliki i zasoby niezbędne do kompilowania program, a także inne ustawienia konfiguracji, na przykład platforma docelowa (x 86, x64 lub ARM) i tego, czy tworzysz Wersja wydana lub z wersji do debugowania programów. Projekt (lub wiele projektów), które są zawarte w *rozwiązania*; na przykład, rozwiązanie może zawierać kilka projektów bibliotek Win32 DLL i jednym Aplikacja konsoli Win32, który używa tych bibliotek DLL. Podczas kompilowania projektu aparat MSBuild zużywa pliku projektu i tworzy plik wykonywalny i/lub wszelkie inne niestandardowe dane wyjściowe wprowadzoną.

Możesz tworzyć projekty Visual C++, wybierając **pliku &#124; New &#124; projektu**, zapewnienie, że zaznaczono Visual C++, w okienku po lewej stronie, a następnie wybierając z listy szablonów projektu w środkowym okienku. Po kliknięciu szablonu w wielu przypadkach pojawi się Kreator, który pozwala ustawić różne właściwości projektu, przed utworzeniem projektu. Można wyświetlić i zmodyfikować te właściwości później za pomocą strony właściwości projektu (**projektu &#124; właściwości**).  
  
 Można również utworzyć nowe projekty przez:  
  
-   Wybieranie **pliku &#124; New &#124; projekt z istniejących źródeł** i postępując zgodnie z instrukcjami w celu dodawania istniejących plików kodu źródłowego. Ta opcja jest najlepsza dla stosunkowo małe i prostych projektach, być może 25 pliki kodów źródłowych lub mniej, za pomocą kilku lub złożonych zależności.  
  
-   począwszy od pliku reguł programu make, a następnie wybierz szablon projektu pliku reguł programu make na karcie Ogólne.  
  
-   Tworzenie pustego projektu (w obszarze **ogólne** kartę) i ręcznego dodawania plików kodu źródłowego, kliknięcie prawym przyciskiem myszy węzeł projektu w Eksploratorze rozwiązań i wybierając pozycję **Dodaj &#124; istniejący element**.  
  
-   za pomocą [Kreatora aplikacji Win32](../windows/win32-application-wizard.md).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Typy projektów Visual C++](../ide/visual-cpp-project-types.md)  
 Zawiera opis typów projektów opartych na platformie MSBuild, które są dostępne w programie Visual C++.  
  
 [Typy plików utworzonych dla projektów Visual C++](../ide/file-types-created-for-visual-cpp-projects.md)  
 W tym artykule opisano rodzaje plików, które są używane z różnymi typami projektów programu MSBuild.  
  
 [Tworzenie projektów wykorzystujących interfejs Pulpitu za pomocą kreatorów aplikacji](../ide/creating-desktop-projects-by-using-application-wizards.md)  
 Jak tworzyć projekty z Visual C++ za pomocą kreatorów.  
  
 [Praca z właściwościami projektu](../ide/working-with-project-properties.md)  
 Opisuje sposób używania arkusze właściwości i strony właściwości, aby określić własne ustawienia projektu.  
  
 [Dodawanie funkcji za pomocą kreatorów kodu](../ide/adding-functionality-with-code-wizards-cpp.md)  
 W tym artykule opisano sposób dodawania do projektu, aby dodać funkcje klas, metod, zmienne i inne elementy.  
  
 [Instrukcje: porządkowanie plików wyjściowych projektu na potrzeby kompilacji](../ide/how-to-organize-project-output-files-for-builds.md)  
 Opisuje sposób organizowania plików wyjściowych projektu.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Kompilowanie programów C/C++](../build/building-c-cpp-programs.md)  
 Zawiera łącza do tematów opisujących, tworzenie programu z wiersza polecenia lub zintegrowanego środowiska projektowego programu Visual Studio.  
  
 [Odwołanie w Visual C++](https://msdn.microsoft.com/1ba03b5c-8229-4f63-b08c-6c12141d6ab1)  
 Zawiera łącza do tematów opisujących C i C++ language odwołania, biblioteki dostarczane z Visual C++, Model obiektowy rozszerzalności Visual C++ i Microsoft Macro Assembler (MASM).  
  
## <a name="see-also"></a>Zobacz też  
 [Visual Studio SDK](https://msdn.microsoft.com/vstudio/extend)
