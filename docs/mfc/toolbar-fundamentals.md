---
title: Podstawowe informacje na temat narzędzi | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- RT_TOOLBAR
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fcb63ade0d1f2ad179448f448a10d88b71b91037
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="toolbar-fundamentals"></a>Paski narzędzi — podstawowe założenia
W tym artykule opisano podstawowe implementacji MFC, które umożliwia dodanie narzędzi domyślne do aplikacji przez wybranie opcji w Kreatorze aplikacji. Tematy obejmują:  
  
-   [Opcja narzędzi Kreatora aplikacji](#_core_the_appwizard_toolbar_option)  
  
-   [Pasek narzędzi w kodzie](#_core_the_toolbar_in_code)  
  
-   [Edytowanie zasobu paska narzędzi](#_core_editing_the_toolbar_resource)  
  
-   [Wiele pasków narzędzi](#_core_multiple_toolbars)  
  
##  <a name="_core_the_appwizard_toolbar_option"></a> Opcja narzędzi Kreatora aplikacji  
 Uzyskanie pojedynczego paska narzędzi z domyślnych przycisków opcję standardowe Dokowanie paska narzędzi na stronie funkcje interfejsu użytkownika z etykietą. To dodaje do aplikacji kod, który:  
  
-   Tworzy obiekt paska narzędzi.  
  
-   Zarządza narzędzi, łącznie z jej możliwości dokowania lub float.  
  
##  <a name="_core_the_toolbar_in_code"></a> Pasek narzędzi w kodzie  
 Pasek narzędzi jest [ctoolbar —](../mfc/reference/ctoolbar-class.md) obiektu zadeklarowany jako element członkowski danych klasy aplikacji **cmainframe —** klasy. Innymi słowy obiekt narzędzi jest osadzony w obiekcie okna w ramce głównej. Oznacza to, że MFC tworzy pasek narzędzi tworzy ramkę okna i niszczy paska narzędzi po jego niszczy okno ramowe. W następującej deklaracji klasy częściowej, wiele aplikacji interfejsu (MDI) dokumentu zawiera elementy członkowskie danych osadzonych narzędzi i paska stanu osadzonych. Przedstawiono również zastąpienia z `OnCreate` funkcję elementu członkowskiego.  
  
 [!code-cpp[NVC_MFCListView#6](../atl/reference/codesnippet/cpp/toolbar-fundamentals_1.h)]  
  
 Tworzenie narzędzi występuje w **CMainFrame::OnCreate**. Wywołania MFC [OnCreate](../mfc/reference/cwnd-class.md#oncreate) po utworzeniu okna ramki, ale przed staje się widoczna. Wartość domyślna `OnCreate` że Kreator aplikacja generuje wykonuje następujące zadania narzędzi:  
  
1.  Wywołania `CToolBar` obiektu [Utwórz](../mfc/reference/ctoolbar-class.md#create) funkcji członkowskiej, aby utworzyć podstawową [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) obiektu.  
  
2.  Wywołania [LoadToolBar](../mfc/reference/ctoolbar-class.md#loadtoolbar) można załadować informacji o zasobie paska narzędzi.  
  
3.  Wywołania funkcji, aby umożliwić dokowania, zmiennoprzecinkowych i etykietki narzędzi. Aby uzyskać więcej informacji o tych wywołań, zobacz artykuł [dokowanie i przestawne paski narzędzi](../mfc/docking-and-floating-toolbars.md).  
  
> [!NOTE]
>  Ogólne MFC próbki [DOCKTOOL](../visual-cpp-samples.md) zawiera ilustracje starych i nowych pasków narzędzi MFC. Paski narzędzi, które używają **coldtoolbar —** wymagają wywołań w kroku 2, aby `LoadBitmap` (zamiast `LoadToolBar`) i `SetButtons`. Nowych pasków narzędzi wymagają wywołań `LoadToolBar`.  
  
 Dokowanie, zmiennoprzecinkowych i wywołania etykietki narzędzia są opcjonalne. Możesz usunąć te wiersze z `OnCreate` Jeśli wolisz. Wynik jest narzędzi, które pozostają stałe, nie można float lub redock i nie można wyświetlić etykietek narzędzi.  
  
##  <a name="_core_editing_the_toolbar_resource"></a> Edytowanie zasobu paska narzędzi  
 Narzędzi domyślne, możesz uzyskać przy użyciu Kreatora aplikacji jest oparta na **rt_toolbar —** zasobów niestandardowych, wprowadzone w MFC w wersji 4.0. Można edytować tego zasobu z [paska narzędzi edytora](../windows/toolbar-editor.md). Edytor umożliwia łatwe dodawanie, usuwanie i rozmieszczanie przycisków. Zawiera ona edytora graficznego w przypadku przycisków, który jest bardzo podobny do edytor grafiki w programie Visual C++. W przypadku edytowania paski narzędzi w poprzednich wersjach programu Visual C++, można znaleźć zadania znacznie łatwiejsze teraz.  
  
 Aby połączyć przycisku paska narzędzi do polecenia, przekażesz przycisku identyfikator polecenia, takich jak `ID_MYCOMMAND`. Określ identyfikator polecenia na stronie właściwości przycisku w edytorze paska narzędzi. Następnie Utwórz funkcję obsługi polecenia (zobacz [mapowanie komunikatów do funkcji](../mfc/reference/mapping-messages-to-functions.md) Aby uzyskać więcej informacji).  
  
 Nowy [ctoolbar —](../mfc/reference/ctoolbar-class.md) funkcje Członkowskie pracować z **rt_toolbar —** zasobów. [LoadToolBar](../mfc/reference/ctoolbar-class.md#loadtoolbar) teraz ma miejsce z [LoadBitmap](../mfc/reference/ctoolbar-class.md#loadbitmap) załadować mapy bitowej obrazy dla przycisków paska narzędzi, a [SetButtons](../mfc/reference/ctoolbar-class.md#setbuttons) stylów przycisków i przyciski Uzyskuj dostęp do map bitowych.  
  
 Aby uzyskać szczegółowe informacje dotyczące korzystania z narzędzi edytora, zobacz [paska narzędzi edytora](../windows/toolbar-editor.md).  
  
##  <a name="_core_multiple_toolbars"></a> Wiele pasków narzędzi  
 Kreator aplikacji zapewnia jeden domyślny paska narzędzi. Jeśli potrzebujesz więcej niż jednego paska narzędzi w aplikacji można modelu kodu dla dodatkowych pasków narzędzi na podstawie kodu generowane przez kreatora domyślne paska narzędzi.  
  
 Jeśli chcesz wyświetlić paska narzędzi w wyniku polecenia, musisz:  
  
-   Utwórz nowy zasób paska narzędzi z paska narzędzi edytora i załaduj go w `OnCreate` z [LoadToolbar](../mfc/reference/ctoolbar-class.md#loadtoolbar) funkcję elementu członkowskiego.  
  
-   Osadzić nowy [ctoolbar —](../mfc/reference/ctoolbar-class.md) obiektu w ramce głównej klasy okna.  
  
-   Sprawdź odpowiednią funkcję wywołuje w `OnCreate` dock lub float pasku narzędzi, ustaw jej style i tak dalej.  
  
### <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o  
  
-   [MFC — implementacja paska narzędzi (omówienie na paskach narzędzi)](../mfc/mfc-toolbar-implementation.md)  
  
-   [Zadokowane i przestawne paski narzędzi](../mfc/docking-and-floating-toolbars.md)  
  
-   [Etykietki narzędzi paska narzędzi](../mfc/toolbar-tool-tips.md)  
  
-   [Ctoolbar —](../mfc/reference/ctoolbar-class.md) i [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) klas  
  
-   [Praca z formantem paska narzędzi](../mfc/working-with-the-toolbar-control.md)  
  
-   [Używanie swoich starych pasków narzędzi](../mfc/using-your-old-toolbars.md)  
  
## <a name="see-also"></a>Zobacz też  
 [MFC, implementacja paska narzędzi](../mfc/mfc-toolbar-implementation.md)

