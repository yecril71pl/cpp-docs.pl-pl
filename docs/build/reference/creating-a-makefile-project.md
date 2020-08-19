---
title: Tworzenie projektu pliku reguł programu make w języku C++ w programie Visual Studio
ms.date: 08/05/2019
f1_keywords:
- vc.appwiz.makefile.project
helpviewer_keywords:
- Makefile projects [C++]
ms.assetid: dd077af3-97a8-48fb-baaa-cf7e07ddef61
ms.openlocfilehash: a712b6da89433b9db6de9f2a676bf6e89d2e0e6e
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/18/2020
ms.locfileid: "88560828"
---
# <a name="create-a-c-makefile-project"></a>Tworzenie projektu pliku reguł programu make języka C++

Plik *reguł programu make* jest plikiem tekstowym zawierającym instrukcje dotyczące kompilowania i łączenia (lub *kompilowania*) zestawu plików kodu źródłowego C++. Program do *wykonywania* odczytuje plik reguł programu make i wywołuje kompilator, konsolidator i inne programy do pliku wykonywalnego. Implementacja programu *Make* firmy Microsoft jest nazywana [NMAKE](nmake-reference.md).

Jeśli masz istniejący projekt pliku reguł programu make, możesz wybrać tę opcję, jeśli chcesz, aby kod i/lub debugować go w środowisku IDE programu Visual Studio:

- Utwórz projekt pliku reguł programu make w programie Visual Studio, który korzysta z istniejącego programu make, aby skonfigurować plik. vcxproj, który będzie używany przez program Visual Studio na potrzeby technologii IntelliSense. (Nie będziesz mieć wszystkich funkcji środowiska IDE, które uzyskasz przy użyciu natywnego projektu MSBuild). Zobacz [, aby utworzyć projekt pliku reguł programu make](#create_a_makefile_project) poniżej.
- Użyj kreatora **tworzenia nowego projektu z istniejących plików z kodem** , aby utworzyć natywny projekt MSBuild na podstawie kodu źródłowego. Oryginalny plik reguł programu make nie zostanie użyty po tym. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie projektu C++ z istniejącego kodu](../how-to-create-a-cpp-project-from-existing-code.md).
- **Visual Studio 2017 i nowsze**: Użyj funkcji **Otwórz folder** , aby edytować i skompilować projekt pliku reguł programu make jako niebędący żadnym udziałem systemu MSBuild. Aby uzyskać więcej informacji, zobacz [Otwieranie projektów folderu dla języka C++](../open-folder-projects-cpp.md).
- **Visual Studio 2019 i nowsze**: Tworzenie projektu pliku reguł programu make dla systemu Linux.

## <a name="a-namecreate_a_makefile_project-to-create-a-makefile-project-with-the-makefile-project-template"></a><a name="create_a_makefile_project"> Aby utworzyć projekt pliku reguł programu make przy użyciu szablonu projektu reguł programu make

W programie Visual Studio 2017 i nowszych szablon projektu pliku reguł programu make jest dostępny po zainstalowaniu obciążenia programowania aplikacji klasycznych w języku C++.

Postępuj zgodnie z instrukcjami kreatora, aby określić polecenia i środowisko używane przez plik reguł programu make. Następnie można użyć tego projektu do kompilowania kodu w programie Visual Studio.

Domyślnie projekt pliku reguł programu make nie wyświetla żadnych plików w Eksplorator rozwiązań. Projekt pliku reguł programu make określa ustawienia kompilacji, które są odzwierciedlone na stronie właściwości projektu.

Plik wyjściowy określany w projekcie nie ma wpływu na nazwę, którą generuje skrypt kompilacji; deklaruje tylko zamiar. Twój plik reguł programu make nadal kontroluje proces kompilacji i określa cele kompilacji.

::: moniker range="vs-2019"

### <a name="to-create-a-makefile-project-in-visual-studio-2019"></a>Aby utworzyć projekt pliku reguł programu make w programie Visual Studio 2019

1. Z menu głównego programu Visual Studio wybierz pozycję **plik**  >  **Nowy**  >  **projekt** i wpisz "make" w polu wyszukiwania. Lub w oknie dialogowym **Nowy projekt** rozwiń węzeł **Visual C++**  >  **Ogólne** (Visual Studio 2015) lub **inny** (Visual Studio 2017), a następnie wybierz jedną z dwóch opcji w zależności od tego, czy będziesz mieć system Windows, czy Linux.

1. **Tylko system Windows**: na stronie **Ustawienia konfiguracji debugowania** podaj informacje o poleceniach, danych wyjściowych, czyszczeniu i odbudowywaniu dla kompilacji do debugowania i sprzedaży detalicznej. Kliknij przycisk **dalej** , jeśli chcesz określić różne ustawienia konfiguracji wydania.

1. Kliknij przycisk **Zakończ** , aby zamknąć okno dialogowe i otworzyć nowo utworzony projekt w **Eksplorator rozwiązań**.

::: moniker-end

::: moniker range="<=vs-2017"

### <a name="to-create-a-makefile-project-in-visual-studio-2015-or-visual-studio-2017"></a>Aby utworzyć projekt pliku reguł programu make w programie Visual Studio 2015 lub Visual Studio 2017

1. Na stronie startowej programu Visual Studio wpisz "plik reguł programu make" w polu wyszukiwania **Nowy projekt** . Lub w oknie dialogowym **Nowy projekt** rozwiń węzeł **Visual C++**  >  **Ogólne** (Visual Studio 2015) lub **inny** (Visual Studio 2017), a następnie wybierz pozycję **Projekt pliku reguł programu make** w okienku szablony, aby otworzyć Kreatora projektu.

1. Na stronie **Ustawienia aplikacji** podaj informacje o poleceniach, danych wyjściowych, czyszczeniu i odbudowywaniu dla kompilacji do debugowania i sprzedaży detalicznej.

1. Kliknij przycisk **Zakończ** , aby zamknąć kreatora i otworzyć nowo utworzony projekt w **Eksplorator rozwiązań**.

::: moniker-end

Możesz przeglądać i modyfikować właściwości projektu na stronie właściwości. Zobacz [Ustawianie właściwości kompilatora i kompilacji C++ w programie Visual Studio](../working-with-project-properties.md) , aby uzyskać informacje o wyświetlaniu strony właściwości.

## <a name="makefile-project-wizard"></a>Kreator projektu pliku reguł programu make

Po utworzeniu projektu pliku reguł programu make można wyświetlić i edytować każdą z poniższych opcji na stronie **NMAKE** na stronie właściwości projektu.

- **Wiersz polecenia kompilacji:** Określa wiersz polecenia do uruchomienia, gdy użytkownik wybierze opcję Kompiluj z menu Kompilacja. Wyświetlane w polu wiersz polecenia kompilacji na stronie NMAKE na stronie właściwości projektu.

- **Dane wyjściowe:** Określa nazwę pliku, który będzie zawierać dane wyjściowe dla wiersza polecenia. Domyślnie ta opcja jest oparta na nazwie projektu. Wyświetlane w polu dane wyjściowe na stronie NMAKE na stronie właściwości projektu.

- **Czyszczenie poleceń:** Określa wiersz polecenia do uruchomienia, gdy użytkownik wybierze opcję Oczyść z menu Kompilacja. Wyświetlany w polu Wyczyść wiersz polecenia na stronie NMAKE na stronie właściwości projektu.

- **Wiersz polecenia ponownego kompilowania:** Określa wiersz polecenia do uruchomienia, gdy użytkownik wybierze opcję Kompiluj ponownie z menu Kompilacja. Wyświetlany w polu Kompiluj ponownie wszystkie wiersze polecenia na stronie NMAKE na stronie właściwości projektu.

## <a name="how-to-enable-intellisense-for-makefile-projects"></a>Porady: włączenie funkcji IntelliSense dla projektów plików reguł programu make

Funkcja IntelliSense w projektach programu make kończy się niepowodzeniem, gdy niektóre ustawienia projektu lub opcje kompilatora są nieprawidłowo skonfigurowane. Wykonaj następujące kroki, aby skonfigurować projekty pliku reguł programu make, tak aby funkcja IntelliSense działała zgodnie z oczekiwaniami:

1. Otwórz okno dialogowe **strony właściwości** . Aby uzyskać szczegółowe informacje, zobacz [Ustawianie kompilatora C++ i właściwości kompilacji w programie Visual Studio](../working-with-project-properties.md).

1. Rozwiń węzeł **Właściwości konfiguracji** .

1. Wybierz stronę właściwości **NMAKE** , a następnie zmodyfikuj odpowiednio właściwości w obszarze **IntelliSense** .

   - Ustaw właściwość **Definicje preprocesora** , aby zdefiniować dowolne symbole preprocesora w projekcie reguł programu make. Aby uzyskać więcej informacji, zobacz [/d (Definicje preprocesora)](d-preprocessor-definitions.md).

   - Ustaw właściwość **Uwzględnij ścieżkę wyszukiwania** , aby określić listę katalogów, które będą wyszukiwane przez kompilator w celu rozpoznania odwołań do plików, które są przesyłane do dyrektyw preprocesora w projekcie reguł programu make. Aby uzyskać więcej informacji, zobacz [/i (Dodatkowe katalogi dołączane)](i-additional-include-directories.md).

   - W przypadku projektów, które są tworzone przy użyciu CL.EXE z okna polecenia, Ustaw zmienną środowiskową **include** , aby określić katalogi, które kompilator będzie przeszukiwać w celu rozpoznania odwołań do plików, które są przesyłane do dyrektyw preprocesora w projekcie programu make.

   - Ustaw właściwość **wymuszone includes** , aby określić, które pliki nagłówkowe mają być przetwarzane podczas kompilowania projektu reguł programu make. Aby uzyskać więcej informacji, zobacz [/Fi (Nazwij plik z wymuszonym dołączeniem)](fi-name-forced-include-file.md).

   - Ustaw właściwość **Ścieżka wyszukiwania zestawu** , aby określić listę katalogów, które będą wyszukiwane przez kompilator w celu rozpoznania odwołań do zestawów .NET w projekcie. Aby uzyskać więcej informacji, zobacz [/AI (Określ katalogi metadanych)](ai-specify-metadata-directories.md).

   - Ustaw właściwość **wymuszone użycie zestawów** , aby określić, które zestawy .NET mają być przetwarzane podczas kompilowania projektu pliku reguł programu make. Aby uzyskać więcej informacji, zobacz [/Fu (nazwa pliku wymuszonego #using)](fu-name-forced-hash-using-file.md).

   - Ustaw właściwość **Opcje dodatkowe** , aby określić dodatkowe przełączniki kompilatora, które mają być używane przez technologię IntelliSense podczas analizowania plików C++.

1. Kliknij przycisk **OK** , aby zamknąć strony właściwości.

1. Użyj polecenia **Zapisz wszystko** , aby zapisać zmodyfikowane ustawienia projektu.

Przy następnym otwarciu projektu pliku reguł programu make w środowisku deweloperskim programu Visual Studio Uruchom polecenie **Oczyść rozwiązanie** , a następnie polecenie **Kompiluj rozwiązanie** w projekcie reguł programu make. Technologia IntelliSense powinna prawidłowo funkcjonować w środowisku IDE.

## <a name="see-also"></a>Zobacz też

[Korzystanie z funkcji IntelliSense](/visualstudio/ide/using-intellisense)<br>
[Odwołanie NMAKE](nmake-reference.md)<br>
[Instrukcje: tworzenie projektu C++ z istniejącego kodu](../how-to-create-a-cpp-project-from-existing-code.md)<br>
[Znaki specjalne w pliku reguł programu make](special-characters-in-a-makefile.md)<br/>
[Zawartość pliku reguł programu make](contents-of-a-makefile.md)<br/>
