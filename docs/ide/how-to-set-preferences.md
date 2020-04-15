---
title: Ustawianie preferencji kodowania języka C++ w programie Visual Studio
ms.description: Customize C++ formatting, colors, layout, line numbers, and menus in the Visual Studio IDE.
ms.topic: overview
ms.date: 09/27/2019
ms.openlocfilehash: e3a665ead7a314b343ec3320e95b189f83a38a47
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365387"
---
# <a name="set-your-c-coding-preferences-in-visual-studio"></a>Ustawianie preferencji kodowania języka C++ w programie Visual Studio

Możesz sprawić, aby kodowanie w języku C++ było wygodniejsze, wydajne i przyjemne, personalizując program Visual Studio. Możesz:

- Dostosuj menu i paski narzędzi.
- Rozmieść układ okna.
- Ustawianie motywów kolorystykowych.
- Określ reguły formatowania języka C++, w tym kilka stylów ClangFormat.
- Tworzenie niestandardowych skrótów klawiaturowych.

Preferencje można synchronizować na wielu komputerach, tworzyć i przechowywać wiele zestawów preferencji oraz udostępniać je kolegom z drużyny. Rozszerzenia można zainstalować z portalu Visual Studio Marketplace, co daje dodatkowe opcje dostosowywania zachowania. Aby uzyskać więcej informacji, zobacz [Personalizowanie ide programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).

## <a name="arrange-window-layout"></a>Rozmieszczanie układu okna

W oknie programu Visual Studio miejsce jest podzielone na menu główne, pasek narzędzi, edytor kodu (lub okno dokumentu) i okna narzędzi (takie jak Eksplorator rozwiązań i lista błędów). Niektóre okna nakładają się na siebie w tej samej pozycji. Na przykład Eksplorator rozwiązań, widok klasy, widok zasobów i Eksplorator kontroli źródła mają tę samą domyślną pozycję. Przełączasz się między nimi, wybierając karty u dołu ramki. Aby co najmniej dwa z tych okien były widoczne w tym samym czasie, wystarczy przeciągnąć jeden z nich za pomocą paska tytułu na nowe miejsce. Można zadokować go przed jednym z krawędzi okna głównego programu Visual Studio lub można go float.

Poniższy zrzut ekranu przedstawia okno **Eksploratora zespołu** przeciągane z jego domyślnej pozycji do nowej, zadokowanego stanowiska po lewej stronie edytora kodu. Niebieski zacieniony obszar pokazuje, gdzie okno zostanie umieszczone po zwolnieniu przycisku myszy.

![Zrzut ekranu przedstawiający okno Eksploratora zespołu programu Visual Studio z wyróżnioną zmianą układu](media/window-layout-move-team-explorer.png)

W oknie dokumentu każdy otwarty plik znajduje się w ramce z kartami. Możesz unosić się lub blokować te karty, podobnie jak okna narzędzi. Aby uzyskać więcej informacji, zobacz [Dostosowywanie układów okien w programie Visual Studio](/visualstudio/ide/customizing-window-layouts-in-visual-studio).

Aby ukryć wszystkie okna narzędzi i zmaksymalizować okno Edytor kodu, naciśnij **klawisz Alt** + **Shift** + **Enter,** aby przełączyć *tryb pełnoekranowy*.

## <a name="set-c-coding-styles-and-formatting"></a>Ustawianie stylów kodowania języka C++ i formatowania

Można określić wiele indywidualnych opcji formatowania kodu, takich jak wcięcie i pozycje nawiasów klamrowych. Aby to zrobić, przejdź do **opcji narzędzia** > **Options** > **Edytor** > tekstu**Formatowanie** **C/C++** > (lub wpisz **Ctrl + Q** i wyszukaj hasło "Formatowanie"). Alternatywnie możesz określić jeden ze stylów [ClangFormat](https://clang.llvm.org/docs/ClangFormat.html) (lub własny niestandardowy styl ClangFormat).

![Zrzut ekranu przedstawiający opcje ClangFormat](media/clang-format-ide.png)

Aby uzyskać więcej informacji na temat wszystkich opcji formatowania, zobacz [Opcje, Edytor tekstu, C/C++, Formatowanie](/visualstudio/ide/reference/options-text-editor-c-cpp-formatting).

## <a name="set-the-color-theme"></a>Ustawianie motywu kolorów

Aby ustawić jasne lub ciemne tło, wpisz **Ctrl + Q** i wyszukaj "Motyw kolorów". Można je również znaleźć, przechodząc do**Environment**środowiska**opcji** >  **narzędzi** > i wybierając opcję Motyw **kolorów**.

![Zrzut ekranu przedstawiający motywy kolorystykowe](media/tools-options-color-theme.png)

Oto na przykład ciemny motyw:

![Zrzut ekranu przedstawiający program Visual Studio z motywem ciemnych kolorów](media/tools-options-dark-theme.png)

## <a name="customize-code-colorization"></a>Dostosowywanie kolorowania kodu

W programie Visual Studio 2019 można wybrać jeden z trzech wstępnie *zdefiniowanych schematów kolorów*. Określają one sposób kolorowania elementów kodu w edytorze. Aby wybrać motyw, przejdź do pozycji**Opcje** >  **narzędzi** > **View**Edytor > **tekstu****Widok C/C++** > i wybierz pozycję **Schemat kolorów**:

![Zrzut ekranu przedstawiający opcje schematu kolorów języka C++ z wyróżnioną rozszerzoną](media/color-schemes.png)

W schemacie kolorów o nazwie **Visual Studio 2017**większość elementów kodu są po prostu czarne. W schematie kolorów **rozszerzonych** funkcje, zmienne lokalne, makra i inne elementy są kolorowane. W systemie **Rozszerzone (Globals vs. Members)** funkcje i zmienne globalne są pokolorowane w celu kontrastu z członkami klasy. Domyślnym trybem jest **Rozszerzony**i wygląda następująco:

![Zrzut ekranu przedstawiający ulepszony schemat kolorów](media/color-scheme-enhanced.png)

Niezależnie od tego, który motyw lub schemat kolorów jest aktywny, można dostosować czcionkę i kolory dla poszczególnych elementów kodu. Aby to zrobić, przejdź do opcji **Narzędzia** > **Options** > **środowiska** > **czcionki i kolory** (lub wpisz **Ctrl + Q** i wyszukaj "Czcionki"). Przewiń w dół listę elementów wyświetlanych, aż zobaczysz opcje języka C++.

![Zrzut ekranu przedstawiający czcionkę i opcje kolorów języka C++](media/tools-options-cpp-colors.png)

Kolory ustawione w tym miejscu zastępują wartości zdefiniowane dla schematów kolorów. Jeśli chcesz wrócić do domyślnych kolorów dla schematu kolorów, ustaw kolor z powrotem na **Domyślny**.

## <a name="customize-the-toolbars"></a>Dostosowywanie pasków narzędzi

Paski narzędzi zapewniają wygodny sposób wydawania poleceń za pomocą jednego kliknięcia, a nie za pomocą menu lub skrótów klawiaturowych. Visual Studio zawiera standardowy zestaw pasków narzędzi. W przypadku standardowego programowania języka C++ najbardziej przydatne paski narzędzi to prawdopodobnie standardowe, edytor tekstu, kompilacja, debugowanie, kontrola źródła i porównywanie plików. W przypadku tworzenia systemu Windows edytor okien dialogowych i edytor obrazów są przydatne do układania okien dialogowych i edytowania ikon.

Umieść wskaźnik myszy na ikonach na pasku narzędzi, aby zobaczyć, które polecenie reprezentuje:

![Zrzut ekranu przedstawiający ikony paska narzędzi z informacjami o poleceniach dostępnych przy najechaniu kursorem](media/toolbar-mouse-hover.png)

Można dodawać lub usuwać polecenia lub tworzyć niestandardowy pasek narzędzi, zaznaczając strzałkę w dół. Aby przenieść pasek narzędzi w nowe miejsce, przeciągnij go za kropkowany pasek po lewej stronie.

![Zrzut ekranu przedstawiający pasek narzędzi z wyróżnioną strzałką w dół i kropkowanym paskiem](media/toolbar-move-edit.png).

Aby uzyskać więcej informacji, zobacz [Jak: Dostosowywanie menu i pasków narzędzi w programie Visual Studio](/visualstudio/ide/how-to-customize-menus-and-toolbars-in-visual-studio).

## <a name="show-or-hide-line-numbers"></a>Pokazywale lub ukrywanie numerów linii

Można określić, czy numery wierszy są wyświetlane po lewej stronie okien edytora. W **obszarze Opcje**w obszarze **C/C++** wybierz pozycję **Ogólne**. W sekcji **Ustawienia** wybierz lub **wyczyść numery linii**, w zależności od preferencji.

![Zrzut ekranu przedstawiający opcje ogólne z wyróżnionymi numerami wierszy](media/tools-options-line-numbers.png)

## <a name="create-keyboard-shortcuts"></a>Tworzenie skrótów klawiaturowych

Wiele poleceń w programie Visual Studio ma *skróty klawiaturowe*, kombinacje klawiszy za pomocą klawiszy Ctrl, Alt i Shift. Można zmodyfikować te skróty klawiaturowe lub utworzyć nowe własne w programie Visual Studio. Przejdź do**klawiatury** **środowiska** > **Opcje** >  **narzędzi** > (lub wpisz **Ctrl + Q** i wyszukaj "skróty"). Aby uzyskać więcej informacji, zobacz [Identyfikowanie i dostosowywanie skrótów klawiaturowych w programie Visual Studio](/visualstudio/ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio).
