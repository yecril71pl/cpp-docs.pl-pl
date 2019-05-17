---
title: Tworzenie projektu pliku reguł programu make w języku C++ w programie Visual Studio
ms.date: 05/16/2019
f1_keywords:
- vc.appwiz.makefile.project
helpviewer_keywords:
- Makefile projects, creating
- project files [C++], Makefile projects
ms.assetid: dd077af3-97a8-48fb-baaa-cf7e07ddef61
ms.openlocfilehash: b460b16b3a64818501187b00e503ad0179d26443
ms.sourcegitcommit: a10c9390413978d36b8096b684d5ed4cf1553bc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2019
ms.locfileid: "65837396"
---
# <a name="create-a-c-makefile-project"></a>Tworzenie projektu pliku reguł programu make w języku C++

A *pliku reguł programu make* to plik tekstowy, który zawiera instrukcje dotyczące sposobu kompilowania i łączenia (lub *kompilacji*) zestaw plików kodu źródłowego języka C++. A *wprowadzić* program odczytuje pliku reguł programu make i wywołuje kompilatora, konsolidatora i ewentualnie inne programy, które się plik wykonywalny. Implementacja firmy Microsoft *wprowadzić* program jest nazywany [NMAKE](nmake-reference.md);

Jeśli masz istniejący projekt pliku reguł programu make, masz te opcje, aby kod i/lub jej debugowania w środowisku IDE programu Visual Studio:

- Utwórz projekt pliku reguł programu make w programie Visual Studio, która używa Twojego istniejącego pliku reguł programu make skonfigurować plik .vcxproj, używanego programu Visual Studio dla technologii IntelliSense. (Nie będziesz mieć wszystkich funkcji środowiska IDE, które otrzymujesz za pomocą natywnego projektu programu MSBuild.) Zobacz [do utworzenia projektu pliku reguł programu make](#create_a_makefile_project) poniżej.
- Użyj **Utwórz nowy projekt z istniejących plików kodu** kreatora w celu utworzenia natywnego projektu programu MSBuild z kodu źródłowego. Oryginalny plik reguł programu make nie będą używane później. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie projektu C++ z istniejącego kodu](../how-to-create-a-cpp-project-from-existing-code.md).
- **Visual Studio 2017 i nowszym**: Użyj **Otwórz Folder** funkcji do edycji i kompilacji projektu pliku reguł programu make jako — bez żadnych zaangażowania systemu MSBuild. Aby uzyskać więcej informacji, zobacz [Otwórz Folder projektów w języku C++](../open-folder-projects-cpp.md).
- **Visual Studio lub nowszy 2019**: Utwórz projekt pliku reguł programu make systemu UNIX dla systemu Linux.

## <a name="a-namecreateamakefileproject-to-create-a-makefile-project-with-the-makefile-project-template"></a><a name="create_a_makefile_project"> Aby utworzyć projekt pliku reguł programu make przy użyciu szablonu projektu pliku reguł programu make

W programie Visual Studio 2017 i nowsze szablon projektu pliku reguł programu make jest dostępna, jeśli zainstalowano obciążenie programowanie aplikacji klasycznych w języku C++.

Użyj kreatora Aby określić polecenia i środowisko używane przez użytkownika pliku reguł programu make. Można następnie użyć tego projektu do kompilacji kodu w programie Visual Studio.

Domyślnie projektu pliku reguł programu make nie wyświetla żadnych plików w Eksploratorze rozwiązań. Projekt pliku reguł programu make określa ustawienia kompilacji, które są odzwierciedlane na stronie właściwości projektu.

Plik wyjściowy określany w projekcie nie ma wpływu na nazwę, którą generuje skrypt kompilacji; deklaruje tylko zamiar. Z pliku reguł programu make nadal kontroluje proces kompilacji, a także określa obiekty docelowe kompilacji.

::: moniker range="vs-2019"

### <a name="to-create-a-makefile-project-in-visual-studio-2019"></a>Aby utworzyć projekt pliku reguł programu make w Visual Studio 2019 r.

1. Wybierz z menu głównego programu Visual Studio **pliku** > **New** > **projektu** i w polu wyszukiwania wpisz "pliku reguł programu make". Lub w **nowy projekt** okna dialogowego rozwiń **Visual C++**   >  **ogólne** (Visual Studio 2015) lub **innych** () Visual Studio 2017) a następnie wybierz pozycję z dwóch opcji, w zależności od tego, czy możesz będą przeznaczone dla Windows lub Linux.

1. **Tylko Windows**: W **ustawienia konfiguracji debugowania** Podaj czyszczenia danych wyjściowych polecenia i ponownej kompilacji informacje dotyczące debugowania i handel detaliczny kompilacje. Kliknij przycisk **dalej** Jeśli chcesz określić różne ustawienia konfiguracji wydania.

1. Kliknij przycisk **Zakończ** aby zamknąć okno dialogowe i otworzyć nowo utworzony projekt w **Eksploratora rozwiązań**.

::: moniker-end

::: moniker range="<=vs-2017"

### <a name="to-create-a-makefile-project-in-visual-studio-2015-or-visual-studio-2017"></a>Aby utworzyć projekt pliku reguł programu make w programie Visual Studio 2015 lub Visual Studio 2017

1. Na stronie początkowej Visual Studio, wpisz "pliku reguł programu make" **nowy projekt** pola wyszukiwania. Lub w **nowy projekt** okna dialogowego rozwiń **Visual C++** > **ogólne** (Visual Studio 2015) lub **innych** (Visual Studio 2017), a następnie wybierz **projektu pliku reguł programu make** w okienku szablonów, aby otworzyć Kreatora projektu.

1. W **ustawienia aplikacji** Podaj czyszczenia danych wyjściowych polecenia i ponownej kompilacji informacje dotyczące debugowania i handel detaliczny kompilacje.

1. Kliknij przycisk **Zakończ** aby zamknąć kreatora i otworzyć nowo utworzony projekt w programie **Eksploratora rozwiązań**.

::: moniker-end

Możesz przeglądać i modyfikować właściwości projektu na stronie właściwości. Zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md) informacje dotyczące wyświetlania strony właściwości.

## <a name="makefile-project-wizard"></a>Kreator projektu pliku reguł programu make

Po utworzeniu projektu pliku reguł programu make, można wyświetlać i edytować każdego z następujących opcji w **Nmake** strony na stronie właściwości projektu.

- **Wiersz polecenia kompilacji:** Określa wiersz polecenia do uruchomienia po użytkownik wybiera kompilacji z menu Kompiluj. Wyświetlana w polu wiersza polecenia kompilacji na stronie Nmake strony właściwości projektu.

- **Dane wyjściowe:** Określa nazwę pliku, który będzie zawierał dane wyjściowe wiersza polecenia. Domyślnie ta opcja opiera się na nazwę projektu. Wyświetlana w polu dane wyjściowe na stronie Nmake strony właściwości projektu.

- **Wyczyść polecenia:** Określa wiersz polecenia do uruchomienia po użytkownik wybiera czysty z menu Kompiluj. Wyświetlana w polu wiersza poleceń oczyszczenia na stronie Nmake strony właściwości projektu.

- **Ponownie skompiluj wiersza polecenia:** Określa wiersz polecenia do uruchomienia po użytkownik wybiera ponowną kompilację z menu Kompiluj. Wyświetlane w rekonstrukcji wszystkie pola w wierszu polecenia na stronie Nmake strony właściwości projektu.

## <a name="how-to-enable-intellisense-for-makefile-projects"></a>Instrukcje: Włączanie funkcji IntelliSense dla projektów plików reguł programu make

Funkcja IntelliSense kończy się niepowodzeniem w przypadku projektów plików reguł programu make podczas niektórych ustawień projektu lub opcje kompilatora są nieprawidłowo skonfigurowana. Wykonaj następujące kroki, aby skonfigurować projektów plików reguł programu make, tak, aby technologia IntelliSense działa zgodnie z oczekiwaniami:

1. Otwórz **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Rozwiń **właściwości konfiguracji** węzła.

1. Wybierz **NMake** właściwości strony, a następnie zmodyfikuj właściwości w obszarze **IntelliSense** odpowiednio.

   - Ustaw **definicje preprocesora** właściwości, aby zdefiniować wszystkie symbole, preprocesor w projekt pliku reguł programu make. Zobacz [/D (definicje preprocesora)](d-preprocessor-definitions.md), aby uzyskać więcej informacji.

   - Ustaw **obejmują ścieżkę wyszukiwania** właściwości w celu określenia listy katalogów, które kompilator będzie przeszukiwał, aby rozwiązać odwołania do plików, które są przekazywane do dyrektywy preprocesora do projektu pliku reguł programu make. Zobacz [/I (dodatkowe katalogi dołączenia)](i-additional-include-directories.md), aby uzyskać więcej informacji.

    - W przypadku projektów, które zostały utworzone przy użyciu CL. Ustaw EXE z poziomu okna polecenia **INCLUDE** zmiennej środowiskowej, aby określić katalogi, które kompilator będzie przeszukiwał, aby rozwiązać odwołania do plików, które są przekazywane do dyrektywy preprocesora do projektu pliku reguł programu make.

   - Ustaw **wymuszone obejmuje** właściwości w celu określenia, który nagłówek plików do przetworzenia podczas kompilowania projektu pliku reguł programu make. Zobacz [/FI (nazwij wymuszone obejmują plik)](fi-name-forced-include-file.md), aby uzyskać więcej informacji.

   - Ustaw **ścieżkę wyszukiwania zestawu** właściwości w celu określenia listy katalogów, które kompilator będzie przeszukiwał, aby rozwiązać odwołania do zestawów .NET w projekcie. Zobacz [/AI (Określ katalogi metadanych)](ai-specify-metadata-directories.md), aby uzyskać więcej informacji.

   - Ustaw **wymuszone za pomocą zestawów** właściwości w celu określenia, które zestawy .NET do przetworzenia podczas kompilowania projektu pliku reguł programu make. Zobacz [/FU (nazwij wymuszone #using)](fu-name-forced-hash-using-file.md), aby uzyskać więcej informacji.

   - Ustaw **dodatkowe opcje** właściwość, aby określić dodatkowe przełączniki kompilatora ma być używany przez funkcję IntelliSense, podczas analizowania plików C++.

1. Kliknij przycisk **OK** zamknąć na stronach właściwości.

1. Użyj **Zapisz wszystko** polecenie, aby zapisać ustawienia modyfikacji projektu.

Przy następnym otwarciu projektu pliku reguł programu make w środowisku programowania Visual Studio Uruchom **czyste rozwiązanie** polecenia i następnie **Kompiluj rozwiązanie** polecenia projektu pliku reguł programu make. Funkcja IntelliSense powinny działać poprawnie w środowisku IDE.

## <a name="see-also"></a>Zobacz także

[Korzystanie z funkcji IntelliSense](/visualstudio/ide/using-intellisense)<br>
[NMAKE — dokumentacja](nmake-reference.md)<br>
[Instrukcje: Tworzenie projektu C++ z istniejącego kodu](../how-to-create-a-cpp-project-from-existing-code.md)
[znaki specjalne w pliku reguł programu make](special-characters-in-a-makefile.md)<br/>
[Zawartość pliku reguł programu Make](contents-of-a-makefile.md)<br/>
