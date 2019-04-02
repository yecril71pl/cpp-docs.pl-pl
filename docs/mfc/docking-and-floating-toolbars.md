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
ms.openlocfilehash: 01450dca56ad662c8db0a35f89749c4a288109b3
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58768137"
---
# <a name="docking-and-floating-toolbars"></a>Zadokowane i przestawne paski narzędzi

Biblioteki klas Microsoft Foundation obsługuje dokowalne pasków narzędzi. Dokowalne narzędzi mogą być dołączone lub zadokowany do dowolnej strony okna nadrzędnego, lub można odłączyć, lub przestawione w osobnym oknie mini ramki. W tym artykule wyjaśniono, jak używać dokowalne paski narzędzi w aplikacjach.

Jeśli Generuj szkielet aplikacji za pomocą Kreatora aplikacji, zostanie wyświetlony monit wybierz, czy dokowalne pasków narzędzi. Domyślnie Kreator aplikacji generuje kod, który wykonuje trzy czynności niezbędna do umieszczenia dokowalne narzędzi w Twojej aplikacji:

- [Włącz dokowania w oknie ramowym](#_core_enabling_docking_in_a_frame_window).

- [Włącz dokowania dla paska narzędzi](#_core_enabling_docking_for_a_toolbar).

- [Dokowanie paska narzędzi (w oknie ramki)](#_core_docking_the_toolbar).

Jeśli brakuje któregokolwiek z tych kroków, aplikacja wyświetli standardowy pasek narzędzi. Ostatnie dwa kroki należy wykonać dla każdego dokowalne paska narzędzi w aplikacji.

Inne tematy omówione w tym artykule obejmują:

- [Przestawne na pasku narzędzi](#_core_floating_the_toolbar)

- [Dynamiczne zmiany rozmiaru na pasku narzędzi](#_core_dynamically_resizing_the_toolbar)

- [Ustawienie zawijania stanowisk dla stałej styl paska narzędzi](#_core_setting_wrap_positions_for_a_fixed_style_toolbar)

Zobacz przykładową ogólne MFC [DOCKTOOL](../overview/visual-cpp-samples.md) przykłady.

##  <a name="_core_enabling_docking_in_a_frame_window"></a> Włączanie dokowania w oknie ramowym

Aby zadokować paski narzędzi w oknie ramowym, należy włączyć okno ramowe (lub docelowego) umożliwia dokowania. Odbywa się przy użyciu [CFrameWnd::EnableDocking](../mfc/reference/cframewnd-class.md#enabledocking) funkcji, która ma jedną *DWORD* parametr, który jest zestawem styl bits, wskazujące, które strony okna ramki akceptuje dokowania. Jeśli ma być zadokowane, pasek narzędzi, a istnieje wiele stron, które może być zadokowane, aby, boki wskazanych w parametr przekazany do `EnableDocking` są używane w następującej kolejności: Góra, dół, lewo, prawo. Jeśli chcesz można było zadokować kontrola pasków dowolnego miejsca, przekazać **CBRS_ALIGN_ANY** do `EnableDocking`.

##  <a name="_core_enabling_docking_for_a_toolbar"></a> Włączanie dokowania dla paska narzędzi

Po przygotowaniu miejsca docelowego dla Dokowanie paska narzędzi (lub źródła) należy przygotować w podobny sposób. Wywołaj [CControlBar::EnableDocking](../mfc/reference/ccontrolbar-class.md#enabledocking) dla każdego paska narzędzi, aby zadokować, miejsce docelowe boków powinien Dokowanie paska narzędzi. Jeśli żaden stron, określone w wywołaniu `CControlBar::EnableDocking` zgodne boki włączone dla dokowania w oknie ramki, pasek narzędzi nie można zadokować — przesunie się. Gdy zostały przestawione, pozostaje swobodny pasek narzędzi, nie można zadokować okno ramek.

Jeśli efekt, chcesz, aby trwale przestawnym narzędzi, wywołaj `EnableDocking` z parametrem 0. Następnie wywołaj [CFrameWnd::FloatControlBar](../mfc/reference/cframewnd-class.md#floatcontrolbar). Pasek narzędzi pozostaje przestawne, trwale nie zadokować w dowolnym miejscu.

##  <a name="_core_docking_the_toolbar"></a> Dokowanie paska narzędzi

Struktura wywołuje [CFrameWnd::DockControlBar](../mfc/reference/cframewnd-class.md#dockcontrolbar) po użytkownik próbuje upuścić na pasku narzędzi na stronie ramki okna, który umożliwia dokowania.

Ponadto możesz wywołać tę funkcję, w dowolnym momencie, aby zadokować okno ramowe paski sterowania. Zazwyczaj można to zrobić podczas inicjowania. Więcej niż jeden pasek narzędzi może być zadokowane do konkretnej strony okna ramki.

##  <a name="_core_floating_the_toolbar"></a> Przestawne na pasku narzędzi

Odłączanie dokowalne narzędzi w oknie ramki jest wywoływana w liczb zmiennoprzecinkowych na pasku narzędzi. Wywołaj [CFrameWnd::FloatControlBar](../mfc/reference/cframewnd-class.md#floatcontrolbar) w tym celu. Określ pasku narzędzi, aby być przestawione, punkt, gdzie ma zostać umieszczony i styl wyrównanie, który określa, czy swobodny pasek narzędzi jest pozioma lub pionowa.

Struktura wywołuje tę funkcję, gdy użytkownik przeciągnie pasek narzędzi poza jego położenie zadokowanego i umieszcza go w lokalizacji, gdzie dokowanie nie jest włączone. Może to być dowolne miejsce wewnątrz lub poza oknem ramki. Podobnie jak w przypadku `DockControlBar`, można również wywołać tę funkcję, podczas inicjowania.

Implementacja MFC dokowalne pasków narzędzi nie zawiera niektóre z rozszerzonych funkcji, które znajdują się w niektórych aplikacjach, które obsługują dokowalne pasków narzędzi. Nie są oferowane w funkcje, takie jak można dostosować paski narzędzi.

##  <a name="_core_dynamically_resizing_the_toolbar"></a> Dynamiczne zmiany rozmiaru na pasku narzędzi

Począwszy od Visual C++ w wersji 4.0 możesz wprowadzić go możliwe dla użytkowników aplikacji, aby dynamicznie Zmień rozmiar przestawne paski narzędzi. Zwykle pasek narzędzi ma kształt długie, liniowej, wyświetlać poziomo. Ale możesz zmienić orientację na pasku narzędzi i jego kształtu. Na przykład po użytkownik dokowane narzędzi względem jednej pionowy strony okna ramki, kształt zostanie zmieniony na układ pionowy. Użytkownik może również zmienić kształt na pasku narzędzi w prostokąt z wielu wierszy przycisków.

Możesz:

- Określ dynamiczna zmiana rozmiaru jako cecha paska narzędzi.

- Określ stały ustalania rozmiaru jako cecha narzędzi.

Aby zapewnić tę obsługę, istnieją dwie nowe style narzędzi do użycia w wywołaniami [CToolBar::Create](../mfc/reference/ctoolbar-class.md#create) funkcja elementu członkowskiego. Są to:

- **CBRS_SIZE_DYNAMIC** pasek sterowania jest dynamiczny.

- **CBRS_SIZE_FIXED** pasek sterowania jest stała.

Style dynamiczne rozmiar informuje użytkownika Zmień rozmiar na pasku narzędzi, jest liczb zmiennoprzecinkowych, ale nie jest zadokowany. Pasek narzędzi "opakowuje" w razie potrzeby można zmienić kształtu, zgodnie z jego krawędzie przeciągania przez użytkownika.

Rozmiar stałej styl zachowuje stany zawijania pasek narzędzi, ustalające położenie przycisków w każdej kolumnie. Użytkownik aplikacji nie może zmienić kształt paska narzędzi. Pasek narzędzi opakowuje w wyznaczonym miejscach, takich jak lokalizacje separatory między przyciskami. Czy pasek narzędzi jest zadokowany lub przestawny, przechowuje tego kształtu. Efekt jest stałym palety z wieloma kolumnami przycisków.

Można również użyć [CToolBar::GetButtonStyle](../mfc/reference/ctoolbar-class.md#getbuttonstyle) do zwrócenia stanu i style przycisków na paski narzędzi. Styl przycisku określa sposób wyświetlania przycisku i sposobu odpowiedzi na dane wejściowe użytkownika Stan informuje, czy przycisk jest w stanie opakowana.

##  <a name="_core_setting_wrap_positions_for_a_fixed_style_toolbar"></a> Ustawienie zawijania stanowisk dla stałej styl paska narzędzi

Dla paska narzędzi o rozmiarze stałej styl wyznaczyć narzędzi przycisk indeksów, w których będzie zawijany w pasku narzędzi. Poniższy kod pokazuje, jak to zrobić w oknie głównym ramki `OnCreate` zastąpienia:

[!code-cpp[NVC_MFCDocViewSDI#10](../mfc/codesnippet/cpp/docking-and-floating-toolbars_1.cpp)]

Próbki MFC-ogólne [DOCKTOOL](../overview/visual-cpp-samples.md) pokazuje, jak używać funkcji elementów członkowskich klas [CControlBar](../mfc/reference/ccontrolbar-class.md) i [CToolBar](../mfc/reference/ctoolbar-class.md) Zarządzanie układ dynamiczny paska narzędzi. Zobacz plik EDITBAR. CPP w DOCKTOOL.

### <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat

- [Podstawowe informacje dotyczące narzędzi](../mfc/toolbar-fundamentals.md)

- [Etykietki narzędzi paska narzędzi](../mfc/toolbar-tool-tips.md)

- [Używanie swoich starych pasków narzędzi](../mfc/using-your-old-toolbars.md)

## <a name="see-also"></a>Zobacz także

[MFC, implementacja paska narzędzi](../mfc/mfc-toolbar-implementation.md)
