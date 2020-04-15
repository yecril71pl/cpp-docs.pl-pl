---
title: Paski narzędzi — podstawowe założenia
ms.date: 11/04/2016
f1_keywords:
- RT_TOOLBAR
helpviewer_keywords:
- embedding toolbar in frame window class [MFC]
- application wizards [MFC], installing default application toolbars
- toolbars [MFC], creating
- resources [MFC], toolbar
- toolbar controls [MFC], toolbars created using Application Wizard
- toolbar controls [MFC], command ID
- RT_TOOLBAR resource [MFC]
- toolbars [MFC], adding default using Application Wizard
- LoadBitmap method [MFC], toolbars
- Toolbar editor [MFC], Application Wizard
- command IDs [MFC], toolbar buttons
- SetButtons method [MFC]
- CToolBar class [MFC], default toolbars in Application Wizard
- frame window classes [MFC], toolbar embedded in
- LoadToolBar method [MFC]
ms.assetid: cc00aaff-8a56-433b-b0c0-b857d76b4ffd
ms.openlocfilehash: d4e8793337beb2eed533fe04daf549ec21efc61d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373481"
---
# <a name="toolbar-fundamentals"></a>Paski narzędzi — podstawowe założenia

W tym artykule opisano podstawową implementację MFC, która umożliwia dodanie domyślnego paska narzędzi do aplikacji przez wybranie opcji w Kreatorze aplikacji. Omawiane tematy to m.in.:

- [Opcja Pasek narzędzi Kreatora aplikacji](#_core_the_appwizard_toolbar_option)

- [Pasek narzędzi w kodzie](#_core_the_toolbar_in_code)

- [Edytowanie zasobu paska narzędzi](#_core_editing_the_toolbar_resource)

- [Wiele pasków narzędzi](#_core_multiple_toolbars)

## <a name="the-application-wizard-toolbar-option"></a><a name="_core_the_appwizard_toolbar_option"></a>Opcja paska narzędzi Kreatora aplikacji

Aby uzyskać pojedynczy pasek narzędzi z przyciskami domyślnymi, wybierz opcję Standardowy pasek narzędzi dokowania na stronie oznaczonej funkcjami interfejsu użytkownika. Spowoduje to dodanie kodu do aplikacji, który:

- Tworzy obiekt paska narzędzi.

- Zarządza paskiem narzędzi, w tym jego zdolność dokowania lub float.

## <a name="the-toolbar-in-code"></a><a name="_core_the_toolbar_in_code"></a>Pasek narzędzi w kodzie

Pasek narzędzi jest [CToolBar](../mfc/reference/ctoolbar-class.md) obiektu zadeklarowanego jako element `CMainFrame` członkowski danych klasy aplikacji. Innymi słowy, obiekt paska narzędzi jest osadzony w obiekcie okna ramki głównej. Oznacza to, że MFC tworzy pasek narzędzi podczas tworzenia okna ramki i niszczy pasek narzędzi, gdy niszczy okno ramki. Następująca deklaracja klasy częściowej dla aplikacji interfejsu wielu dokumentów (MDI) zawiera elementy członkowskie danych dla osadzonego paska narzędzi i osadzonego paska stanu. Pokazuje również zastąpienie funkcji elementu `OnCreate` członkowskiego.

[!code-cpp[NVC_MFCListView#6](../atl/reference/codesnippet/cpp/toolbar-fundamentals_1.h)]

Tworzenie paska `CMainFrame::OnCreate`narzędzi odbywa się w pliku . MFC wywołuje [OnCreate](../mfc/reference/cwnd-class.md#oncreate) po utworzeniu okna dla ramki, ale zanim stanie się widoczna. `OnCreate` Domyślnie generowany przez Kreatora aplikacji wykonuje następujące zadania paska narzędzi:

1. Wywołuje `CToolBar` funkcję elementu członkowskiego [Create](../mfc/reference/ctoolbar-class.md#create) obiektu, aby utworzyć podstawowy [obiekt CToolBarCtrl.](../mfc/reference/ctoolbarctrl-class.md)

1. Wywołuje [LoadToolBar,](../mfc/reference/ctoolbar-class.md#loadtoolbar) aby załadować informacje o zasobie paska narzędzi.

1. Wywołuje funkcje, aby włączyć dokowanie, przestawne i porady narzędzi. Aby uzyskać szczegółowe informacje na temat tych połączeń, zobacz artykuł [Dokowanie i pływające paski narzędzi](../mfc/docking-and-floating-toolbars.md).

> [!NOTE]
> Przykładowy [docktool](../overview/visual-cpp-samples.md) MFC zawiera ilustracje zarówno starych, jak i nowych pasków narzędzi MFC. Paski narzędzi, które `COldToolbar` używają wymagają wywołań `LoadBitmap` w `LoadToolBar`kroku 2 do (a nie) i do `SetButtons`. Nowe paski narzędzi wymagają `LoadToolBar`wywołania .

Wywołania dokowania, przestawne i porady narzędzia są opcjonalne. Możesz usunąć te `OnCreate` wiersze, jeśli wolisz. Rezultatem jest pasek narzędzi, który pozostaje stały, nie może unosić się w powietrzu lub redokować i nie może wyświetlać końcówek narzędzi.

## <a name="editing-the-toolbar-resource"></a><a name="_core_editing_the_toolbar_resource"></a>Edytowanie zasobu paska narzędzi

Domyślny pasek narzędzi, który można uzyskać za pomocą Kreatora aplikacji jest oparty na **RT_TOOLBAR** zasobu niestandardowego, wprowadzony w wersji MFC 4.0. Zasób ten można edytować za pomocą [edytora paska narzędzi](../windows/toolbar-editor.md). Edytor umożliwia łatwe dodawanie, usuwanie i zmienianie rozmieszczenia przycisków. Zawiera edytor graficzny dla przycisków, który jest bardzo podobny do edytora grafiki ogólnej w języku Visual C++. Jeśli edytowano paski narzędzi w poprzednich wersjach programu Visual C++, zadanie będzie teraz znacznie łatwiejsze.

Aby podłączyć przycisk paska narzędzi do polecenia, należy nadać `ID_MYCOMMAND`przyciskowi identyfikator polecenia, na przykład . Określ identyfikator polecenia na stronie właściwości przycisku w edytorze paska narzędzi. Następnie utwórz funkcję obsługi dla polecenia (zobacz [Mapowanie wiadomości do funkcji, aby](../mfc/reference/mapping-messages-to-functions.md) uzyskać więcej informacji).

Nowe funkcje członkowskie [CToolBar](../mfc/reference/ctoolbar-class.md) działają z zasobem **RT_TOOLBAR.** [LoadToolBar](../mfc/reference/ctoolbar-class.md#loadtoolbar) zajmuje teraz miejsce [LoadBitmap,](../mfc/reference/ctoolbar-class.md#loadbitmap) aby załadować bitmapę obrazów przycisków paska narzędzi, a [Przyciski SetButtons,](../mfc/reference/ctoolbar-class.md#setbuttons) aby ustawić style przycisków i połączyć przyciski z obrazami bitmapowymi.

Aby uzyskać szczegółowe informacje na temat korzystania z edytora paska narzędzi, zobacz [Edytor paska narzędzi](../windows/toolbar-editor.md).

## <a name="multiple-toolbars"></a><a name="_core_multiple_toolbars"></a>Wiele pasków narzędzi

Kreator aplikacji udostępnia jeden domyślny pasek narzędzi. Jeśli potrzebujesz więcej niż jednego paska narzędzi w aplikacji, można modelować kod dla dodatkowych pasków narzędzi na podstawie kodu wygenerowanego przez kreatora dla domyślnego paska narzędzi.

Jeśli chcesz wyświetlić pasek narzędzi w wyniku polecenia, musisz:

- Utwórz nowy zasób paska narzędzi za `OnCreate` pomocą edytora paska narzędzi i załaduj go za pomocą funkcji elementu członkowskiego [LoadToolbar.](../mfc/reference/ctoolbar-class.md#loadtoolbar)

- Osadź nowy [obiekt CToolBar](../mfc/reference/ctoolbar-class.md) w klasie okna ramki głównej.

- Wykonuj `OnCreate` odpowiednie wywołania funkcji, aby zadokować lub upłynąć na pasku narzędzi, ustawić jego style i tak dalej.

### <a name="what-do-you-want-to-know-more-about"></a>Co chcesz wiedzieć więcej o

- [Implementacja paska narzędzi MFC (informacje ogólne dotyczące pasków narzędzi)](../mfc/mfc-toolbar-implementation.md)

- [Dokowanie i pływające paski narzędzi](../mfc/docking-and-floating-toolbars.md)

- [Wskazówki dotyczące narzędzi paska narzędzi](../mfc/toolbar-tool-tips.md)

- Klasy [CToolBar](../mfc/reference/ctoolbar-class.md) i [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)

- [Praca z kontrolką paska narzędzi](../mfc/working-with-the-toolbar-control.md)

- [Korzystanie ze starych pasków narzędzi](../mfc/using-your-old-toolbars.md)

## <a name="see-also"></a>Zobacz też

[MFC, implementacja paska narzędzi](../mfc/mfc-toolbar-implementation.md)
