---
title: Typy projektów Visual C++
ms.date: 11/29/2018
helpviewer_keywords:
- programs [C++], projects
- project templates [Visual Studio], C++
- TODO comments [C++]
- projects [C++], types
- templates [C++], projects
- applications [C++], projects
- C++ projects, types
ms.assetid: 7337987e-1e7b-4120-9a4b-94f0401f15e7
ms.openlocfilehash: dce96a221804e5538929d63fa3c125a27e7fc36d
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2019
ms.locfileid: "65217774"
---
# <a name="c-project-templates"></a>Szablony projektów języka C++

Szablony projektu Visual Studio generować pliki kodu źródłowego, opcje kompilatora, menu, paski narzędzi, ikony, odwołania i `#include` instrukcji, które są odpowiednie dla rodzaju projektu, w której chcesz utworzyć. Program Visual Studio zawiera kilka rodzajów z C++ szablony projektów i zapewnia kreatory dla wielu z nich, dzięki czemu można dostosować swoje projekty, jak można je utworzyć. Bezpośrednio po utworzeniu projektu, można ją skompilować i uruchomić aplikację; jest dobrą praktyką, aby tworzyć sporadycznie podczas opracowywania aplikacji.

> [!NOTE]
> Można utworzyć projektu języka C przy użyciu szablonów projektów języka C++. W wygenerowanego projektu Zlokalizuj pliki .cpp, rozszerzenie nazwy pliku i zmień go na. c. Następnie na **właściwości projektu** strony dla projektu (a nie dla rozwiązania), a następnie rozwiń **właściwości konfiguracji**, **C/C++** i wybierz **zaawansowane**. Zmiana **kompilacji jako** ustawienie **skompiluj jako kod języka C (/ TC)**.

## <a name="project-templates"></a>Szablony projektów

Szablony projektów zawarte w Visual Studio zależy od tego, wersja produktu i obciążeń, które zostały zainstalowane. Jeśli po zainstalowaniu programowanie aplikacji klasycznych w języku C++ obciążenie, program Visual Studio zawiera te C++ szablony projektów.

### <a name="windows-desktop"></a>Windows Desktop

|Szablon projektu|Opis|
|----------------------|-----------------------------|
|[Aplikacja Konsolowa Windows](../../windows/creating-a-console-application.md)|Projekt służący do tworzenia aplikacji konsolowej Windows.|
|[Windows aplikacji klasycznych](../../windows/walkthrough-creating-windows-desktop-applications-cpp.md)|Projekt służący do tworzenia aplikacji pulpitu (Win32) Windows.|
|[Biblioteka dołączana dynamicznie](../walkthrough-creating-and-using-a-dynamic-link-library-cpp.md)|Projekt służący do tworzenia biblioteki dołączanej (dynamicznie DLL).|
|[Biblioteka statyczna](../../windows/walkthrough-creating-and-using-a-static-library-cpp.md)|Projekt służący do tworzenia biblioteki statycznej (LIB).|
|Kreator aplikacji klasycznej Windows|Kreator do tworzenia aplikacji klasycznych Windows i biblioteki za pomocą dodatkowych opcji.|

### <a name="general"></a>Ogólne

|Szablon projektu|Opis|
|----------------------|-----------------------------|
|Pusty projekt|Pusty projekt do tworzenia aplikacji, biblioteki lub bibliotekę DLL. Należy dodać żaden kod lub wymaganych zasobów.|
|[Projekt pliku reguł programu make](creating-a-makefile-project.md)|Projekt, który otacza Windows pliku reguł programu make w projekcie programu Visual Studio. (Aby otworzyć pliku reguł programu make — w programie Visual Studio, użyj [Otwórz Folder](../open-folder-projects-cpp.md).|
|Projekt elementów udostępnionych|Projekt używany do udostępniania plików kodu lub zasobów między wieloma projektami. Ten typ projektu nie generuje plik wykonywalny.|

### <a name="atl"></a>ATL

|Szablon projektu|Opis|
|----------------------|-----------------------------|
|[ATL Project](../../atl/reference/creating-an-atl-project.md)|Projekt, który korzysta z biblioteki Active Template Library.|

### <a name="test"></a>Test

|Szablon projektu|Opis|
|----------------------|-----------------------------|
|[Native Unit Test Project](/visualstudio/test/writing-unit-tests-for-c-cpp-with-the-microsoft-unit-testing-framework-for-cpp)|Projekt zawierający testy jednostkowe w usłudze natywnego języka C++.|

### <a name="mfc"></a>MFC

Jeśli dodasz obsługę MFC i ATL składników do instalacji programu Visual Studio, te szablony projektów są dodawane do programu Visual Studio.

|Szablon projektu|Opis|
|----------------------|-----------------------------|
|[Aplikacja MFC](../../mfc/reference/creating-an-mfc-application.md)|Projekt służący do tworzenia aplikacji, która używa biblioteki Microsoft Foundation Class (MFC).|
|[Kontrolki ActiveX MFC](../../mfc/reference/creating-an-mfc-activex-control.md)|Projekt służący do tworzenia formantu ActiveX, który korzysta z biblioteki MFC.|
|[BIBLIOTEKI MFC DLL](../../mfc/reference/creating-an-mfc-dll-project.md)|Projekt służący do tworzenia biblioteki dll, która używa biblioteki MFC.|

### <a name="windows-universal-apps"></a>Windows Universal Apps

Jeśli dodasz składnik narzędzia platformy uniwersalnej dla Windows C++ do instalacji programu Visual Studio tych szablonów projektu zostaną dodane do programu Visual Studio.

Omówienie Windows Universal apps w języku C++, zobacz [Universal Windows Apps (C++)](../../windows/universal-windows-apps-cpp.md).

|Szablon projektu|Opis|
|----------------------|-----------------------------|
|Pusta aplikacja|Projekt jednostronicowej aplikacji uniwersalnej platformy Windows (UWP), który nie ma wstępnie zdefiniowanych kontrolek ani układu.|
|Aplikacja DirectX 11|Projekt aplikacji uniwersalnej platformy Windows, który używa programu DirectX 11.|
|DirectX 12 App|Projekt aplikacji uniwersalnej platformy Windows, który używa programu DirectX 12.|
|DirectX 11 i XAML aplikacji|Projekt dla aplikacji Universal Windows Platform, który używa programu DirectX 11 i XAML.|
|Aplikacja testów jednostkowych|Projekt służący do tworzenia aplikacji testów jednostkowych dla aplikacji uniwersalnych platformy Windows (UWP).|
|DLL|Projekt natywnej biblioteki dołączanej (dynamicznie DLL) używany przez platformę Windows uniwersalną aplikację lub składnik środowiska uruchomieniowego.|
|Biblioteka statyczna|Projekt macierzystej biblioteki dołączanej (statycznie LIB) używany przez platformę Windows uniwersalną aplikację lub składnik środowiska uruchomieniowego.|
|Składnik środowiska wykonawczego systemu Windows|Projekt składnika środowiska wykonawczego Windows, który może być używany przez aplikację Universal Windows Platform, niezależnie od języka programowania, w którym napisano aplikację.|
|Projekt pakietu aplikacji Windows|Projekt, który tworzy pakiet platformy uniwersalnej systemu Windows, który umożliwia aplikacji klasycznej ładowanych lub rozproszonego przy użyciu Microsoft Store.|

## <a name="todo-comments"></a>Komentarze TODO

Wiele plików wygenerowanych przez szablon projektu zawiera komentarze TODO, aby pomóc w zidentyfikowaniu, w którym można podać kod źródłowy. Aby uzyskać więcej informacji na temat dodawania kodu, zobacz [Dodawanie funkcji z kreatorami kodów](../../ide/adding-functionality-with-code-wizards-cpp.md) i [Praca z plikami zasobów](../../windows/working-with-resource-files.md).


