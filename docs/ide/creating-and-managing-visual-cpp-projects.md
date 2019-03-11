---
title: Tworzenie projektów Visual C++ i zarządzanie nimi
ms.date: 11/04/2016
f1_keywords:
- vcprojects
- creatingmanagingVC
helpviewer_keywords:
- ATL projects, creating
- Visual C++ projects, creating
- projects [C++], creating
- Visual C++ projects
- ATL projects
ms.assetid: 11003cd8-9046-4630-a189-a32bf3b88047
ms.openlocfilehash: e511ef597e64a3782ce7a3ce650db065e9299cdd
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/11/2019
ms.locfileid: "57744327"
---
# <a name="creating-and-managing-msbuild-based-visual-c-projects"></a>Tworzenie i zarządzanie projektami opartych na platformie MSBuild Visual C++

Program MSBuild jest system kompilacji natywne w języku Visual C++ i zazwyczaj najlepsze kompilacji systemowi operacyjnemu używanie dla aplikacji platformy uniwersalnej systemu Windows, a także aplikacji pulpitu, które używają biblioteki ATL i MFC. Program MSBuild jest ściśle zintegrowana za pomocą środowiska IDE programu Visual Studio i system projektu, ale można go także użyć w wierszu polecenia. Począwszy od programu Visual Studio 2017, Visual C++ obsługuje [CMake i innych systemów innych niż MSBuild, za pomocą funkcji Otwórz Folder](non-msbuild-projects.md).

Z opartych na platformie MSBuild projekt zawiera plik projektu w formacie XML (.vcxproj), która określa wszystkie pliki i zasoby niezbędne do kompilowania program, a także inne ustawienia konfiguracji, na przykład platforma docelowa (x 86, x64 lub ARM) i tego, czy tworzysz Wersja wydana lub z wersji do debugowania programów. Projekt (lub wiele projektów), które są zawarte w *rozwiązania*; na przykład, rozwiązanie może zawierać kilka projektów bibliotek Win32 DLL i jednym Aplikacja konsoli Win32, który używa tych bibliotek DLL. Podczas kompilowania projektu aparat MSBuild zużywa pliku projektu i tworzy plik wykonywalny i/lub wszelkie inne niestandardowe dane wyjściowe wprowadzoną.

Możesz tworzyć projekty Visual C++, wybierając **pliku &#124; New &#124; projektu**, zapewnienie, że zaznaczono Visual C++, w okienku po lewej stronie, a następnie wybierając z listy szablonów projektu w środkowym okienku. Po kliknięciu szablonu w wielu przypadkach pojawi się Kreator, który pozwala ustawić różne właściwości projektu, przed utworzeniem projektu. Można wyświetlić i zmodyfikować te właściwości później za pomocą strony właściwości projektu (**projektu &#124; właściwości**).

Można również utworzyć nowe projekty przez:

- Wybieranie **pliku &#124; New &#124; projekt z istniejących źródeł** i postępując zgodnie z instrukcjami w celu dodawania istniejących plików kodu źródłowego. Ta opcja jest najlepsza dla stosunkowo małe i prostych projektach, być może 25 pliki kodów źródłowych lub mniej, za pomocą kilku lub złożonych zależności.

- począwszy od pliku reguł programu make, a następnie wybierz szablon projektu pliku reguł programu make na karcie Ogólne.

- Tworzenie pustego projektu (w obszarze **ogólne** kartę) i ręcznego dodawania plików kodu źródłowego, kliknięcie prawym przyciskiem myszy węzeł projektu w Eksploratorze rozwiązań i wybierając pozycję **Dodaj &#124; istniejący element**.

- za pomocą [Kreatora aplikacji Win32](../windows/win32-application-wizard.md).

## <a name="in-this-section"></a>W tej sekcji

[Typy projektów Visual C++](../ide/visual-cpp-project-types.md)<br>
Zawiera opis typów projektów opartych na platformie MSBuild, które są dostępne w programie Visual C++.

[Typy plików utworzonych dla projektów Visual C++](../ide/file-types-created-for-visual-cpp-projects.md)<br>
W tym artykule opisano rodzaje plików, które są używane z różnymi typami projektów programu MSBuild.

[Tworzenie projektów wykorzystujących interfejs Pulpitu za pomocą kreatorów aplikacji](../ide/creating-desktop-projects-by-using-application-wizards.md)<br>
Jak tworzyć projekty z Visual C++ za pomocą kreatorów.

[Praca z właściwościami projektu](../ide/working-with-project-properties.md)<br>
Opisuje sposób używania arkusze właściwości i strony właściwości, aby określić własne ustawienia projektu.

[Dodawanie funkcji za pomocą kreatorów kodu](../ide/adding-functionality-with-code-wizards-cpp.md)<br>
W tym artykule opisano sposób dodawania do projektu, aby dodać funkcje klas, metod, zmienne i inne elementy.

[Instrukcje: Porządkowanie plików wyjściowych projektu na potrzeby kompilacji](../ide/how-to-organize-project-output-files-for-builds.md)<br>
Opisuje sposób organizowania plików wyjściowych projektu.

## <a name="related-sections"></a>Sekcje pokrewne

[Kompilowanie programów C/C++](../build/building-c-cpp-programs.md)<br>
Zawiera łącza do tematów opisujących, tworzenie programu z wiersza polecenia lub zintegrowanego środowiska projektowego programu Visual Studio.

## <a name="see-also"></a>Zobacz także

[Visual Studio SDK](https://msdn.microsoft.com/vstudio/extend)
