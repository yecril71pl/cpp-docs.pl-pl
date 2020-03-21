---
title: Typy projektów Visual C++
ms.date: 08/13/2019
helpviewer_keywords:
- programs [C++], projects
- project templates [Visual Studio], C++
- TODO comments [C++]
- projects [C++], types
- templates [C++], projects
- applications [C++], projects
- C++ projects, types
ms.assetid: 7337987e-1e7b-4120-9a4b-94f0401f15e7
ms.openlocfilehash: f322d16bbbe91d229fb8efdfb5f2d35cb0a686ae
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "80079224"
---
# <a name="c-project-templates"></a>Szablony projektów w języku C++

Szablony projektu programu Visual Studio generują pliki kodu źródłowego, opcje kompilatora, menu, paski narzędzi, ikony, odwołania i instrukcje `#include`, które są odpowiednie dla rodzaju projektu, który chcesz utworzyć. Program Visual Studio zawiera kilka rodzajów C++ szablonów projektów i udostępnia kreatorów dla wielu z nich, aby można było dostosować projekty podczas ich tworzenia. Natychmiast po utworzeniu projektu można skompilować i uruchomić aplikację. dobrym sposobem jest utworzenie nieprzerwanie podczas opracowywania aplikacji.

> [!NOTE]
> Projekt języka C można utworzyć przy użyciu C++ szablonów projektu. W wygenerowanym projekcie zlokalizuj pliki o rozszerzeniu nazwy pliku. cpp i zmień je na. c. Następnie na stronie **właściwości projektu** dla projektu (nie dla rozwiązania) rozwiń węzeł **Właściwości konfiguracji**, **C++ C/** i wybierz pozycję **Zaawansowane**. Zmień ustawienie **Kompiluj jako** na **Kompiluj jako kod C (/TC)** .

## <a name="project-templates"></a>Szablony projektów

Szablony projektu zawarte w programie Visual Studio zależą od wersji produktu i zainstalowanych obciążeń. Jeśli zainstalowano Tworzenie aplikacji klasycznych C++ przy użyciu obciążenia, program Visual C++ Studio ma te szablony projektów.

### <a name="windows-desktop"></a>Pulpit systemu Windows

|Szablon projektu|Opis|
|----------------------|-----------------------------|
|[Aplikacja konsolowa systemu Windows](../../windows/creating-a-console-application.md)|Projekt służący do tworzenia aplikacji konsolowej systemu Windows.|
|[Aplikacja klasyczna systemu Windows](../../windows/walkthrough-creating-windows-desktop-applications-cpp.md)|Projekt służący do tworzenia aplikacji klasycznej systemu Windows (Win32).|
|[Biblioteka dołączana dynamicznie](../walkthrough-creating-and-using-a-dynamic-link-library-cpp.md)|Projekt służący do tworzenia biblioteki dołączanej dynamicznie (DLL).|
|[Biblioteka statyczna](../../windows/walkthrough-creating-and-using-a-static-library-cpp.md)|Projekt służący do tworzenia biblioteki statycznej (LIB).|
|[Kreator aplikacji klasycznej systemu Windows](../../windows/windows-desktop-wizard.md)|Kreator do tworzenia aplikacji klasycznych i bibliotek systemu Windows z dodatkowymi opcjami.|

### <a name="general"></a>Ogólne

|Szablon projektu|Opis|
|----------------------|-----------------------------|
|Pusty projekt|Pusty projekt służący do tworzenia aplikacji, biblioteki lub biblioteki DLL. Należy dodać wymagany kod lub zasoby.|
|[Projekt pliku reguł programu make](creating-a-makefile-project.md)|Projekt, który otacza plik reguł programu make systemu Windows w projekcie programu Visual Studio. (Aby otworzyć plik reguł programu make w programie Visual Studio, użyj [apletu Otwórz folder](../open-folder-projects-cpp.md).|
|Projekt elementów udostępnionych|Projekt używany do udostępniania plików kodu lub plików zasobów między wieloma projektami. Ten typ projektu nie tworzy pliku wykonywalnego.|

### <a name="atl"></a>ATL

|Szablon projektu|Opis|
|----------------------|-----------------------------|
|[Projekt ATL](../../atl/reference/creating-an-atl-project.md)|Projekt, który używa Active Template Library.|

### <a name="test"></a>Testowanie

|Szablon projektu|Opis|
|----------------------|-----------------------------|
|[Natywny projekt testów jednostkowych](/visualstudio/test/writing-unit-tests-for-c-cpp-with-the-microsoft-unit-testing-framework-for-cpp)|Projekt, który zawiera natywne C++ testy jednostkowe.|

### <a name="mfc"></a>MFC

Jeśli dodasz składnik obsługi MFC i ATL do instalacji programu Visual Studio, te szablony projektu zostaną dodane do programu Visual Studio.

|Szablon projektu|Opis|
|----------------------|-----------------------------|
|[Aplikacja MFC](../../mfc/reference/creating-an-mfc-application.md)|Projekt służący do tworzenia aplikacji, która korzysta z biblioteki Microsoft Foundation Class (MFC).|
|[Kontrolka ActiveX MFC](../../mfc/reference/creating-an-mfc-activex-control.md)|Projekt do tworzenia kontrolki ActiveX korzystającej z biblioteki MFC.|
|[BIBLIOTEKA DLL MFC](../../mfc/reference/creating-an-mfc-dll-project.md)|Projekt służący do tworzenia biblioteki dołączanej dynamicznie, która używa biblioteki MFC.|

### <a name="windows-universal-apps"></a>Aplikacje uniwersalne systemu Windows

W przypadku dodania składnika C++ narzędzia platformy uniwersalnej systemu Windows do instalacji programu Visual Studio te szablony projektu zostaną dodane do programu Visual Studio.

Aby zapoznać się z omówieniem uniwersalnych aplikacji C++systemu Windows w programie, zobacz [aplikacje uniwersalne systemu WindowsC++()](../../cppcx/universal-windows-apps-cpp.md).

|Szablon projektu|Opis|
|----------------------|-----------------------------|
|Pusta aplikacja|Projekt dla jednostronicowej aplikacji platforma uniwersalna systemu Windows (platformy UWP), która nie ma wstępnie zdefiniowanych kontrolek ani układu.|
|Aplikacja DirectX 11|Projekt aplikacji platforma uniwersalna systemu Windowsej, który używa programu DirectX 11.|
|Aplikacja DirectX 12|Projekt aplikacji platforma uniwersalna systemu Windows, który używa programu DirectX 12.|
|Aplikacja DirectX 11 i XAML|Projekt aplikacji platforma uniwersalna systemu Windows, który używa programu DirectX 11 i języka XAML.|
|Aplikacja testów jednostkowych|Projekt służący do tworzenia aplikacji testów jednostkowych dla aplikacji platforma uniwersalna systemu Windows (platformy UWP).|
|DLL|Projekt natywnej biblioteki dołączanej dynamicznie (DLL), która może być używana przez aplikację platforma uniwersalna systemu Windows lub składnik środowiska uruchomieniowego.|
|Biblioteka statyczna|Projekt natywnej biblioteki dołączanej statycznie (LIB), która może być używana przez aplikację platforma uniwersalna systemu Windows lub składnik środowiska uruchomieniowego.|
|Składnik środowiska wykonawczego systemu Windows|Projekt składnika środowisko wykonawcze systemu Windows, który może być używany przez aplikację platforma uniwersalna systemu Windows, niezależnie od języka programowania, w którym napisano aplikację.|
|Projekt pakietu aplikacji systemu Windows|Projekt tworzący pakiet platformy UWP, który umożliwia aplikacjom klasycznym ładowanie lub dystrybuowanie za pośrednictwem Microsoft Store.|

## <a name="todo-comments"></a>Komentarze do zrobienia

Wiele plików generowanych przez szablon projektu zawiera komentarze do zrobienia, które ułatwiają określenie, gdzie można podać własny kod źródłowy. Aby uzyskać więcej informacji na temat dodawania kodu, zobacz [Dodawanie funkcji za pomocą kreatorów kodu](../../ide/adding-functionality-with-code-wizards-cpp.md) i [Praca z plikami zasobów](../../windows/working-with-resource-files.md).
