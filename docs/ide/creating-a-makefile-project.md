---
title: Tworzenie projektu pliku reguł programu make w języku C++ | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/12/2018
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.appwiz.makefile.project
dev_langs:
- C++
helpviewer_keywords:
- Makefile projects, creating
- project files [C++], Makefile projects
ms.assetid: dd077af3-97a8-48fb-baaa-cf7e07ddef61
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3be9c22302bc693c44293266ea49ca97fae54f82
ms.sourcegitcommit: b4432d30f255f0cb58dce69cbc8cbcb9d44bc68b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2018
ms.locfileid: "45535059"
---
# <a name="creating-a-c-makefile-project"></a>Tworzenie projektu pliku reguł programu make w języku C++

A *pliku reguł programu make* to plik tekstowy, który zawiera instrukcje dotyczące sposobu kompilowania i łączenia (lub *kompilacji*) zestaw plików kodu źródłowego języka C++. A *wprowadzić* program odczytuje pliku reguł programu make i wywołuje kompilatora, konsolidatora i ewentualnie inne programy, które się plik wykonywalny. Implementacja firmy Microsoft *wprowadzić* program jest nazywany **NMAKE**. (Program visual Studio domyślnie używa system MSBuild na podstawie plików .vcsproj; jest to, co jest tworzone przez **pliku | Nowe | Projekt**.)

Jeśli masz istniejący projekt pliku reguł programu make, masz te opcje, aby kod i/lub jej debugowania w środowisku IDE programu Visual Studio: 

- Utwórz projekt pliku reguł programu make w programie Visual Studio korzysta z istniejących plików reguł programu make do kompilacji kodu w środowisku IDE. (Nie będziesz mieć wszystkich funkcji środowiska IDE, które otrzymujesz za pomocą natywnego projektu programu MSBuild.) Zobacz [do utworzenia projektu pliku reguł programu make](#create_a_makefile_project) poniżej.
- Użyj **Utwórz nowy projekt z istniejących plików kodu** kreatora w celu utworzenia natywnego projektu programu MSBuild z kodu źródłowego. Aby uzyskać więcej informacji, zobacz [porady: Tworzenie projektu C++ z istniejącego kodu](how-to-create-a-cpp-project-from-existing-code.md). 
- **Visual Studio 2017 i nowszym**: Użyj **Otwórz Folder** funkcji można otworzyć pliku reguł programu make. Aby uzyskać więcej informacji, zobacz [projekty Otwórz Folder w programie Visual C++](non-msbuild-projects.md).

## <a name="a-namecreateamakefileproject-to-create-a-makefile-project-with-the-makefile-project-template"></a><a name="create_a_makefile_project"> Aby utworzyć projekt pliku reguł programu make przy użyciu szablonu projektu pliku reguł programu make

W programie Visual Studio 2017 i nowsze szablon projektu pliku reguł programu make jest dostępna, jeśli zainstalowano obciążenie programowanie aplikacji klasycznych w języku C++. 

Użyj kreatora Aby określić polecenia i środowisko używane przez użytkownika pliku reguł programu make. Można następnie użyć tego projektu do kompilacji kodu w środowisku programowania Visual Studio. 

Domyślnie projektu pliku reguł programu make nie wyświetla żadnych plików w Eksploratorze rozwiązań. Projekt pliku reguł programu make określa ustawienia kompilacji, które są odzwierciedlane na stronie właściwości projektu.

Plik wyjściowy określany w projekcie nie ma wpływu na nazwę, którą generuje skrypt kompilacji; deklaruje tylko zamiar. Z pliku reguł programu make nadal kontroluje proces kompilacji, a także określa obiekty docelowe kompilacji.

1. Na stronie początkowej Visual Studio, wpisz "pliku reguł programu make" **nowy projekt** pola wyszukiwania. Lub w **nowy projekt** okna dialogowego rozwiń **Visual C++** > **ogólne** (Visual Studio 2015) lub **innych** (Visual Studio 2017), a następnie wybierz **projektu pliku reguł programu make** w okienku szablonów, aby otworzyć Kreatora projektu.

1. W [ustawienia aplikacji](../ide/application-settings-makefile-project-wizard.md) Podaj czyszczenia danych wyjściowych polecenia i ponownej kompilacji informacje dotyczące debugowania i handel detaliczny kompilacje.

1. Kliknij przycisk **Zakończ** aby zamknąć kreatora i otworzyć nowo utworzony projekt w programie **Eksploratora rozwiązań**.

Możesz przeglądać i modyfikować właściwości projektu na stronie właściwości. Zobacz [ustawienie właściwości projektu Visual C++](../ide/working-with-project-properties.md) informacje dotyczące wyświetlania strony właściwości.

## <a name="see-also"></a>Zobacz też

[Kreator projektu pliku reguł programu make](../ide/makefile-project-wizard.md)<br/>
[Znaki specjalne w pliku reguł programu Make](../build/special-characters-in-a-makefile.md)<br/>
[Zawartość pliku reguł programu Make](../build/contents-of-a-makefile.md)<br/>
