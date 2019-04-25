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
ms.openlocfilehash: 9c784db2e1a482b313147e6837d6bbbd16d0ecb4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62168222"
---
# <a name="toolbar-fundamentals"></a>Paski narzędzi — podstawowe założenia

W tym artykule opisano podstawowe implementacja MFC, które umożliwia dodanie narzędzi domyślne do aplikacji, zaznaczając odpowiednią opcję w Kreatorze aplikacji. Omawiane tematy to m.in.:

- [Opcja narzędzi Kreatora aplikacji](#_core_the_appwizard_toolbar_option)

- [Pasek narzędzi w kodzie](#_core_the_toolbar_in_code)

- [Edytowanie zasób paska narzędzi](#_core_editing_the_toolbar_resource)

- [Wiele pasków narzędzi](#_core_multiple_toolbars)

##  <a name="_core_the_appwizard_toolbar_option"></a> Opcja narzędzi Kreatora aplikacji

Aby uzyskać jednym pasku narzędzi, za pomocą przycisków domyślne, wybierz standardowego dokowania paska narzędzi na stronie opcji etykietą funkcje interfejsu użytkownika. Spowoduje to dodanie kodu do aplikacji który:

- Tworzy obiekt paska narzędzi.

- Zarządza narzędzi, łącznie z jego możliwości, aby zadokować lub liczb zmiennoprzecinkowych.

##  <a name="_core_the_toolbar_in_code"></a> Pasek narzędzi w kodzie

Pasek narzędzi jest [CToolBar](../mfc/reference/ctoolbar-class.md) obiekt zadeklarowany jako element członkowski danych Twojej aplikacji `CMainFrame` klasy. Innymi słowy obiekt paska narzędzi jest osadzony w obiekcie ramką głównego okna. Oznacza to, MFC utworzoną za pomocą paska narzędzi tworzy okno ramowe i niszczy pasek narzędzi, gdy jej niszczy okno ramowe. W następującej deklaracji klasy częściowej, wielu dokumentów (MDI) aplikację z interfejsem, zawiera elementy członkowskie danych osadzonym pasku narzędzi i pasek stanu osadzonych. Zawiera również zastępowania metody `OnCreate` funkcja elementu członkowskiego.

[!code-cpp[NVC_MFCListView#6](../atl/reference/codesnippet/cpp/toolbar-fundamentals_1.h)]

Tworzenie narzędzi występuje w `CMainFrame::OnCreate`. Wywołania MFC [OnCreate](../mfc/reference/cwnd-class.md#oncreate) po utworzeniu okna ramki, ale przed staje się widoczny. Wartość domyślna `OnCreate` , Kreator aplikacji generuje wykonuje następujące zadania narzędzi:

1. Wywołania `CToolBar` obiektu [Utwórz](../mfc/reference/ctoolbar-class.md#create) funkcja elementu członkowskiego, aby utworzyć podstawową [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) obiektu.

1. Wywołania [LoadToolBar](../mfc/reference/ctoolbar-class.md#loadtoolbar) można załadować informacji o zasobie paska narzędzi.

1. Wywołuje funkcje umożliwiające dokowania, zmiennoprzecinkowe i etykietek narzędzi. Aby uzyskać szczegółowe informacje o tych wywołań, zobacz artykuł [dokowanie i przestawne paski narzędzi](../mfc/docking-and-floating-toolbars.md).

> [!NOTE]
>  Próbki MFC-ogólne [DOCKTOOL](../overview/visual-cpp-samples.md) obejmuje ilustracje starych i nowych pasków narzędzi MFC. Paski narzędzi, które używają `COldToolbar` wymagają wywołań w kroku 2, aby `LoadBitmap` (zamiast `LoadToolBar`) i `SetButtons`. Nowych pasków narzędzi wymagają wywołań `LoadToolBar`.

Dokowanie, liczb zmiennoprzecinkowych i narzędzie porady wywołania są opcjonalne. Możesz usunąć te wiersze z `OnCreate` Jeśli użytkownik sobie tego życzy. Wynik jest pasek narzędzi, który pozostaje stały, mógł zmiennoprzecinkowego lub redock i nie można wyświetlić etykietek narzędzi.

##  <a name="_core_editing_the_toolbar_resource"></a> Edytowanie zasób paska narzędzi

Domyślne paska narzędzi, możesz uzyskać za pomocą Kreatora aplikacji opiera się na **rt_toolbar —** zasobów niestandardowych, wprowadzona w MFC w wersji 4.0. Możesz edytować ten zasób z [Edytor paska narzędzi](../windows/toolbar-editor.md). Edytor pozwala łatwo dodawać, usuwać i rozmieszczanie przycisków. Zawiera ona edytor graficzny dla przycisków, który jest bardzo podobny do edytora grafiki w programie Visual C++. Jeśli edytowano paski narzędzi w poprzednich wersjach programu Visual C++, można znaleźć zadania znacznie łatwiejsze teraz.

Aby połączyć przycisku paska narzędzi z poleceniem, nadasz przycisku identyfikator polecenia, takie jak `ID_MYCOMMAND`. Określ identyfikator polecenia na stronie właściwości przycisku paska narzędzi edytora. Następnie Utwórz funkcję obsługi polecenia (zobacz [mapowanie komunikatów do funkcji](../mfc/reference/mapping-messages-to-functions.md) Aby uzyskać więcej informacji).

Nowe [CToolBar](../mfc/reference/ctoolbar-class.md) elementów członkowskich pracować **rt_toolbar —** zasobów. [LoadToolBar](../mfc/reference/ctoolbar-class.md#loadtoolbar) teraz zajmuje miejsce [loadbitmap —](../mfc/reference/ctoolbar-class.md#loadbitmap) można załadować mapy bitowej przycisku paska narzędzi obrazów, i [setbuttons —](../mfc/reference/ctoolbar-class.md#setbuttons) stylów przycisków i skupionej przyciski obrazy mapy bitowej.

Aby uzyskać szczegółowe informacje dotyczące korzystania z narzędzi edytora, zobacz [Edytor paska narzędzi](../windows/toolbar-editor.md).

##  <a name="_core_multiple_toolbars"></a> Wiele pasków narzędzi

Kreator aplikacji zapewnia jeden domyślny narzędzi. Jeśli potrzebujesz więcej niż jednego paska narzędzi w aplikacji można modelować swój kod pod kątem dodatkowe paski narzędzi, na podstawie kodu generowane przez kreatora dla paska narzędzi domyślne.

Jeśli chcesz wyświetlić pasek narzędzi w wyniku polecenia, musisz:

- Utwórz nowy zasób paska narzędzi z paska narzędzi edytora i załaduj go w `OnCreate` z [LoadToolbar](../mfc/reference/ctoolbar-class.md#loadtoolbar) funkcja elementu członkowskiego.

- Osadzanie nowej [CToolBar](../mfc/reference/ctoolbar-class.md) obiektów w klasie ramką głównego okna.

- Marka, wywołuje odpowiednią funkcję `OnCreate` zadokować lub float pasek narzędzi, ustawianie jego stylów i tak dalej.

### <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat

- [MFC — implementacja paska narzędzi (informacje ogólne na paskach narzędzi)](../mfc/mfc-toolbar-implementation.md)

- [Zadokowane i przestawne paski narzędzi](../mfc/docking-and-floating-toolbars.md)

- [Etykietki narzędzi paska narzędzi](../mfc/toolbar-tool-tips.md)

- [CToolBar](../mfc/reference/ctoolbar-class.md) i [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) klas

- [Praca z formantem paska narzędzi](../mfc/working-with-the-toolbar-control.md)

- [Używanie swoich starych pasków narzędzi](../mfc/using-your-old-toolbars.md)

## <a name="see-also"></a>Zobacz także

[MFC, implementacja paska narzędzi](../mfc/mfc-toolbar-implementation.md)
