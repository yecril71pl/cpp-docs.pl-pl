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
ms.openlocfilehash: b3afbd2019965d859895462cfdad57292bc2e0b3
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "33332426"
---
# <a name="creating-and-managing-msbuild-based-visual-c-projects"></a>Tworzenie projektów i zarządzanie nimi na podstawie MSBuild Visual C++
MSBuild system natywnej kompilacji dla programu Visual C++ oraz jest zazwyczaj najlepiej systemu na potrzeby aplikacji platformy uniwersalnej systemu Windows, a także aplikacji klasycznych, które używają biblioteki MFC lub ATL kompilacji. MSBuild jest ściśle zintegrowany z programu Visual Studio IDE i system projektu, ale można również użyć go w wierszu polecenia. Począwszy od programu Visual Studio 2017 Visual C++ obsługuje [CMake i innych systemów innych niż MSBuild za pomocą funkcji Otwórz Folder](non-msbuild-projects.md).

Plik projektu w formacie XML (.vcxproj), który określa wszystkich plików i zasobów potrzebnych do skompilowania programu, a także innych ustawień konfiguracyjnych, na przykład platformy docelowej (x 86, x64 lub ARM) i określa, czy tworzysz ma projektu MSBuild Wersja wydana lub wersja do debugowania programu. Projekt (lub wiele projektów), które są zawarte w *rozwiązania*, na przykład rozwiązanie może zawierać kilka projektów Win32 DLL i jednej aplikacji konsoli Win32, która używa tych bibliotek DLL. Podczas kompilowania projektu aparat MSBuild zużywa pliku projektu i tworzy plik wykonywalny i/lub innych niestandardowych wyjściowego określona.

Projekty Visual C++ można utworzyć, wybierając **pliku &#124; nowy &#124; projektu**, zapewnienie, że wybrano Visual C++, w okienku po lewej stronie, a następnie wybierając z listy szablonów projektu w środkowym okienku. Po kliknięciu szablonu w wielu przypadkach pojawi się Kreator umożliwiający ustawić różne właściwości projektu, przed utworzeniem projektu. Możesz wyświetlić i później zmodyfikować te właściwości, za pomocą stron właściwości projektu (**projektu &#124; właściwości**).  
  
 Można również tworzyć nowe projekty przez:  
  
-   Wybieranie **pliku &#124; nowy &#124; projekt z istniejących źródeł** i zgodnie z monitami, aby dodać istniejących plików kodu źródłowego. Ta opcja działa najlepiej dla projektów stosunkowo małe i proste, prawdopodobnie 25 plików kodów źródłowych lub z kilku lub złożonych zależności.  
  
-   rozpoczyna się od pliku reguł programu make i wybierz szablon projektu pliku reguł programu make na karcie Ogólne.  
  
-   pusty projekt do tworzenia (w obszarze **ogólne** kartę) i ręczne dodanie plików kodu źródłowego prawym przyciskiem myszy węzeł projektu w Eksploratorze rozwiązań i wybierając pozycję **Dodaj &#124; istniejący element**.  
  
-   przy użyciu [Kreator aplikacji Win32](../windows/win32-application-wizard.md).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Typy projektów Visual C++](../ide/visual-cpp-project-types.md)  
 W tym artykule opisano typy projektu MSBuild, które są dostępne w programie Visual C++.  
  
 [Typy plików utworzonych dla projektów Visual C++](../ide/file-types-created-for-visual-cpp-projects.md)  
 W tym artykule opisano typy plików, które są używane z różnymi typami projektu MSBuild.  
  
 [Tworzenie projektów wykorzystujących interfejs Pulpitu za pomocą kreatorów aplikacji](../ide/creating-desktop-projects-by-using-application-wizards.md)  
 Sposób tworzenia projektów w języku Visual C++ za pomocą kreatorów.  
  
 [Praca z właściwościami projektu](../ide/working-with-project-properties.md)  
 Opisuje sposób użycia właściwości strony i arkusze właściwości do określenia ustawień projektu.  
  
 [Dodawanie funkcji z kreatorami kodów](../ide/adding-functionality-with-code-wizards-cpp.md)  
 Opisuje sposób dodawania klas, metod, zmienne i inne elementy do projektu, aby dodać funkcje.  
  
 [Instrukcje: porządkowanie plików wyjściowych projektu na potrzeby kompilacji](../ide/how-to-organize-project-output-files-for-builds.md)  
 Opisuje sposób porządkowanie plików wyjściowych projektu.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Kompilowanie programów C/C++](../build/building-c-cpp-programs.md)  
 Zawiera łącza do tematów opisujących kompilowania programu z wiersza polecenia lub zintegrowane środowisko programistyczne Visual Studio.  
  
 [Dokumentacja języka Visual C++](http://msdn.microsoft.com/en-us/1ba03b5c-8229-4f63-b08c-6c12141d6ab1)  
 Zawiera łącza do tematów opisujących C i C++ języka odwołań, bibliotek języka Visual C++, Visual C++ modelu obiektów rozszerzających i asemblera makr firmy Microsoft (MASM).  
  
## <a name="see-also"></a>Zobacz też  
 [Visual Studio SDK](http://msdn.microsoft.com/vstudio/extend)
