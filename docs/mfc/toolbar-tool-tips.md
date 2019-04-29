---
title: Etykietki narzędzi paska narzędzi
ms.date: 11/04/2016
helpviewer_keywords:
- tool tips [MFC], activating
- CBRS_TOOLTIPS constant [MFC]
- tool tips [MFC], adding text
- updates [MFC]
- CBRS_FLYBY constant [MFC]
- tool tips [MFC]
- updating status bar messages
- updates, status bar messages
- status bars [MFC], tool tips
- flyby status bar updates
ms.assetid: d1696305-b604-4fad-9f09-638878371412
ms.openlocfilehash: 4582b03844e1be3d4cf70bcc3fff1c3b66119ae3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62351777"
---
# <a name="toolbar-tool-tips"></a>Etykietki narzędzi paska narzędzi

Etykietki narzędzi są niewielki rozmiar okna podręcznego systemu windows, są one krótkie opisy przeznaczenia przycisku paska narzędzi, gdy umieszczenie wskaźnika myszy nad przyciskiem w okresie czasu. Podczas tworzenia aplikacji za pomocą Kreatora aplikacji, które ma pasek narzędzi, wsparcie Porada jest dostarczany. W tym artykule opisano zarówno narzędzia Porada pomocy technicznej utworzonych przez Kreatora aplikacji oraz jak dodać obsługę Porada narzędzie do aplikacji.

W tym artykule omówiono:

- [Aktywowanie etykietek narzędzi](#_core_activating_tool_tips)

- [Aktualizacje paska stanu flyby —](#_core_fly_by_status_bar_updates)

##  <a name="_core_activating_tool_tips"></a> Aktywowanie etykietek narzędzi

Aby aktywować etykietki narzędzia w aplikacji, należy wykonać dwie czynności:

- Dodaj CBRS_TOOLTIPS style do innych stylów (takich jak WS_CHILD, WS_VISIBLE i inne **CBRS_** style) przekazany jako *dwStyle* parametr [CToolBar::Create](../mfc/reference/ctoolbar-class.md#create) Funkcja lub [SetBarStyle](../mfc/reference/ccontrolbar-class.md#setbarstyle).

- Zgodnie z opisem w poniższej procedurze, należy dołączyć tekst porady narzędzi, oddzielone znakiem nowego wiersza ('\n'), do zasobu ciągu zawierającego wiersz polecenia dla polecenia narzędzi. Zasób ciągu udziałów identyfikator przycisku paska narzędzi.

#### <a name="to-add-the-tool-tip-text"></a>Aby dodać tekst wskazówki

1. Gdy edytujesz narzędzi w edytorze paska narzędzi, otwórz **właściwości przycisku paska narzędzi** okna dla danego przycisku.

1. W **monitu** Określ tekst, który ma być wyświetlany w etykietce narzędzia dla tego przycisku.

> [!NOTE]
>  Ustawienie tekstu jako właściwości przycisku paska narzędzi edytora zastępuje wcześniejsze procedury, w którym trzeba było otworzyć i edytować zasobu ciągu.

Jeśli pasek sterowania z etykietek narzędzi włączone zawiera formanty podrzędne dla niej, pasek sterowania zostanie wyświetlona etykietka narzędzia dla każdego formantu podrzędnego, na pasku sterowania, tak długo, jak spełnia następujące kryteria:

- Identyfikator formantu jest - 1.

- Zapis tabeli ciągów mających taki sam identyfikator jak kontrolki podrzędnej w pliku zasobów ma ciągu etykietki narzędzia.

##  <a name="_core_fly_by_status_bar_updates"></a> Pasek stanu flyby — aktualizacje

"Flyby —" stanu paska aktualizacji jest wyświetlana funkcji związanych z etykietek narzędzi. Domyślnie komunikat na pasku stanu w tym artykule opisano tylko przycisku paska narzędzi w szczególności gdy przycisk jest aktywny. Umieszczając CBRS_FLYBY na liście style przekazany do `CToolBar::Create`, mogą mieć tych komunikatów aktualizowane, gdy kursor myszy przesuwa się nad pasek narzędzi bez faktycznego aktywowania przycisku.

### <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat

- [MFC — implementacja paska narzędzi (informacje ogólne na paskach narzędzi)](../mfc/mfc-toolbar-implementation.md)

- [Zadokowane i przestawne paski narzędzi](../mfc/docking-and-floating-toolbars.md)

- [CToolBar](../mfc/reference/ctoolbar-class.md) i [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) klas

- [Praca z formantem paska narzędzi](../mfc/working-with-the-toolbar-control.md)

- [Używanie swoich starych pasków narzędzi](../mfc/using-your-old-toolbars.md)

## <a name="see-also"></a>Zobacz także

[MFC, implementacja paska narzędzi](../mfc/mfc-toolbar-implementation.md)
