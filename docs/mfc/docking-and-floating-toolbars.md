---
title: Zadokowane i przestawne paski narzędzi
ms.date: 11/04/2016
f1_keywords:
- CBRS_SIZE_DYNAMIC
- CBRS_SIZE_FIXED
helpviewer_keywords:
- size [MFC], toolbars
- size
- frame windows [MFC], toolbar docking
- CBRS_ALIGN_ANY constant [MFC]
- palettes, floating
- toolbars [MFC], docking
- CBRS_SIZE_DYNAMIC constant [MFC]
- floating toolbars
- toolbars [MFC], size
- toolbars [MFC], floating
- fixed-size toolbars
- CBRS_SIZE_FIXED constant [MFC]
- toolbar controls [MFC], wrapping
- toolbars [MFC], wrapping
- floating palettes
ms.assetid: b7f9f9d4-f629-47d2-a3c4-2b33fa6b51e4
ms.openlocfilehash: 30113565167b96b0df84a65768a1dfabe92ceffe
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369772"
---
# <a name="docking-and-floating-toolbars"></a>Zadokowane i przestawne paski narzędzi

Biblioteka klas programu Microsoft Foundation obsługuje dokowane paski narzędzi. Dockable pasek narzędzi może być dołączony lub zadokowany, do dowolnej strony okna nadrzędnego, lub może być odłączony lub floated, we własnym oknie mini-ramki. W tym artykule wyjaśniono, jak używać dokowania pasków narzędzi w aplikacjach.

Jeśli używasz Kreatora aplikacji do generowania szkieletu aplikacji, zostaniesz poproszony o wybranie, czy mają być zadokowane paski narzędzi. Domyślnie Kreator aplikacji generuje kod, który wykonuje trzy akcje niezbędne do umieszczenia dokowania paska narzędzi w aplikacji:

- [Włącz dokowanie w oknie ramki](#_core_enabling_docking_in_a_frame_window).

- [Włącz dokowanie paska narzędzi](#_core_enabling_docking_for_a_toolbar).

- [Zadokuj pasek narzędzi (do okna ramki).](#_core_docking_the_toolbar)

Jeśli brakuje któregokolwiek z tych kroków, aplikacja wyświetli standardowy pasek narzędzi. Ostatnie dwa kroki muszą być wykonywane dla każdego dokowania paska narzędzi w aplikacji.

Inne tematy omówione w tym artykule obejmują:

- [Przesuwanie paska narzędzi](#_core_floating_the_toolbar)

- [Dynamiczna zmiana rozmiaru paska narzędzi](#_core_dynamically_resizing_the_toolbar)

- [Ustawianie pozycji zawijania dla paska narzędzi o stałym stylu](#_core_setting_wrap_positions_for_a_fixed_style_toolbar)

Zobacz przykłady MFC General [DOCKTOOL.](../overview/visual-cpp-samples.md)

## <a name="enabling-docking-in-a-frame-window"></a><a name="_core_enabling_docking_in_a_frame_window"></a>Włączanie dokowania w oknie ramki

Aby zadokować paski narzędzi do okna ramki, okno ramki (lub miejsce docelowe) musi być włączone, aby umożliwić dokowanie. Odbywa się to za pomocą [CFrameWnd::EnableDocking](../mfc/reference/cframewnd-class.md#enabledocking) funkcji, która przyjmuje jeden *parametr DWORD,* który jest zestaw bitów stylu wskazując, która strona okna ramki akceptuje dokowania. Jeśli pasek narzędzi ma być zadokowany i istnieje wiele stron, do których można go `EnableDocking` zadokować, boki wskazane w parametrze przekazanym są używane w następującej kolejności: góra, dół, lewa, prawa. Jeśli chcesz mieć możliwość dokowania pasków sterujących `EnableDocking`w dowolnym miejscu, przekaż **CBRS_ALIGN_ANY** do .

## <a name="enabling-docking-for-a-toolbar"></a><a name="_core_enabling_docking_for_a_toolbar"></a>Włączanie dokowania dla paska narzędzi

Po przygotowaniu miejsca docelowego do dokowania należy przygotować pasek narzędzi (lub źródło) w podobny sposób. Wywołanie [CControlBar::EnableDocking](../mfc/reference/ccontrolbar-class.md#enabledocking) dla każdego paska narzędzi, który chcesz zadokować, określając boki docelowe, do których pasek narzędzi powinien zadokować. Jeśli żadna ze stron określonych `CControlBar::EnableDocking` w wywołaniu, aby dopasować boki włączone do dokowania w oknie ramki, pasek narzędzi nie może zadokować — będzie float. Po jego floated, pozostaje pływający pasek narzędzi, nie można zadokować do okna ramki.

Jeśli żądany efekt jest stale przestawnym `EnableDocking` paskiem narzędzi, wywołanie z parametrem 0. Następnie zadzwoń [CFrameWnd::FloatControlBar](../mfc/reference/cframewnd-class.md#floatcontrolbar). Pasek narzędzi pozostaje zmienny, trwale nie może dokować w dowolnym miejscu.

## <a name="docking-the-toolbar"></a><a name="_core_docking_the_toolbar"></a>Dokowanie paska narzędzi

Struktura wywołuje [CFrameWnd::DockControlBar,](../mfc/reference/cframewnd-class.md#dockcontrolbar) gdy użytkownik próbuje upuścić pasek narzędzi z boku okna ramki, który umożliwia dokowanie.

Ponadto można wywołać tę funkcję w dowolnym momencie, aby zadokować paski sterujące do okna ramki. Zwykle odbywa się to podczas inicjowania. Więcej niż jeden pasek narzędzi można zadokować do określonej strony okna ramki.

## <a name="floating-the-toolbar"></a><a name="_core_floating_the_toolbar"></a>Przesuwanie paska narzędzi

Odłączanie dokowania paska narzędzi od okna ramki nazywa się przesuwaniem paska narzędzi. Wywołanie [CFrameWnd::FloatControlBar](../mfc/reference/cframewnd-class.md#floatcontrolbar) w tym celu. Określ pasek narzędzi, który ma być unoszony, punkt, w którym ma być umieszczony, oraz styl wyrównania określający, czy ruchomy pasek narzędzi jest poziomy czy pionowy.

Struktura wywołuje tę funkcję, gdy użytkownik przeciąga pasek narzędzi poza zadokowany lokalizacja i upuszcza go w lokalizacji, w której dokowanie nie jest włączone. Może to być w dowolnym miejscu wewnątrz lub na zewnątrz okna ramy. Podobnie `DockControlBar`jak w tym, można również wywołać tę funkcję podczas inicjowania.

Implementacja MFC dockable paski narzędzi nie zapewnia niektóre z rozszerzonych funkcji znalezionych w niektórych aplikacjach, które obsługują dokowane paski narzędzi. Funkcje, takie jak konfigurowalne paski narzędzi, nie są dostarczane.

## <a name="dynamically-resizing-the-toolbar"></a><a name="_core_dynamically_resizing_the_toolbar"></a>Dynamiczna zmiana rozmiaru paska narzędzi

Od wersji 4.0 visual C++ można umożliwić użytkownikom aplikacji dynamiczne zmiany rozmiaru ruchomych pasków narzędzi. Zazwyczaj pasek narzędzi ma długi, liniowy kształt wyświetlany w poziomie. Można jednak zmienić orientację i kształt paska narzędzi. Na przykład, gdy użytkownik dokuje pasek narzędzi względem jednej z pionowych boków okna ramki, kształt zmienia się w układ pionowy. Istnieje również możliwość przekształcenia paska narzędzi w prostokąt z wieloma wierszami przycisków.

Możesz:

- Określ dynamiczne określanie rozmiaru jako charakterystykę paska narzędzi.

- Określ stałą charakterystykę rozmiaru jako paska narzędzi.

Aby zapewnić tę obsługę, istnieją dwa nowe style paska narzędzi do użycia w wywołaniach [funkcji CToolBar::Create](../mfc/reference/ctoolbar-class.md#create) member. Oto one:

- **CBRS_SIZE_DYNAMIC** Pasek sterowania jest dynamiczny.

- **CBRS_SIZE_FIXED** Pasek sterowania jest stały.

Styl dynamiczny rozmiaru umożliwia użytkownikowi zmienianie rozmiaru paska narzędzi, gdy jest on przestawny, ale nie gdy jest zadokowany. Pasek narzędzi "zawija się" tam, gdzie jest to konieczne, aby zmienić kształt, gdy użytkownik przeciąga jego krawędzie.

Styl stały rozmiar zachowuje stany zawijania paska narzędzi, ustalając położenie przycisków w każdej kolumnie. Użytkownik aplikacji nie może zmienić kształtu paska narzędzi. Pasek narzędzi jest zawijany w wyznaczonych miejscach, takich jak lokalizacje separatorów między przyciskami. Zachowuje ten kształt, niezależnie od tego, czy pasek narzędzi jest zadokowany, czy przestawny. Efektem jest stała paleta z wieloma kolumnami przycisków.

Można również użyć [CToolBar::GetButtonStyle,](../mfc/reference/ctoolbar-class.md#getbuttonstyle) aby zwrócić stan i styl dla przycisków na paskach narzędzi. Styl przycisku określa, jak przycisk jest wyświetlany i jak reaguje na dane wejściowe użytkownika; stan informuje, czy przycisk jest w stanie zawiniętym.

## <a name="setting-wrap-positions-for-a-fixed-style-toolbar"></a><a name="_core_setting_wrap_positions_for_a_fixed_style_toolbar"></a>Ustawianie pozycji zawijania dla paska narzędzi o stałym stylu

W przypadku paska narzędzi o stałym rozmiarze oznaczaj indeksy przycisków paska narzędzi, na których pasek narzędzi zostanie zawinięty. Poniższy kod pokazuje, jak to zrobić w `OnCreate` zastąpieniu okna ramki głównej:

[!code-cpp[NVC_MFCDocViewSDI#10](../mfc/codesnippet/cpp/docking-and-floating-toolbars_1.cpp)]

Przykładowy [docktool](../overview/visual-cpp-samples.md) MFC pokazuje, jak używać funkcji członkowskich klas [CControlBar](../mfc/reference/ccontrolbar-class.md) i [CToolBar](../mfc/reference/ctoolbar-class.md) do zarządzania dynamicznym układem paska narzędzi. Zobacz plik EDITBAR. CPP w DOCKTOOL.

### <a name="what-do-you-want-to-know-more-about"></a>Co chcesz wiedzieć więcej o

- [Podstawy paska narzędzi](../mfc/toolbar-fundamentals.md)

- [Wskazówki dotyczące narzędzi paska narzędzi](../mfc/toolbar-tool-tips.md)

- [Korzystanie ze starych pasków narzędzi](../mfc/using-your-old-toolbars.md)

## <a name="see-also"></a>Zobacz też

[MFC, implementacja paska narzędzi](../mfc/mfc-toolbar-implementation.md)
