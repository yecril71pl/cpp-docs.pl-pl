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
ms.openlocfilehash: 1762931b75734801659fd6271377260bd0473614
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373455"
---
# <a name="toolbar-tool-tips"></a>Etykietki narzędzi paska narzędzi

Wskazówki dotyczące narzędzi to małe okna podręczne, które przedstawiają krótkie opisy celu przycisku paska narzędzi po umieszczeniu myszy nad przyciskiem przez pewien czas. Podczas tworzenia aplikacji za pomocą Kreatora aplikacji, który ma pasek narzędzi, obsługa etykietki narzędzia jest dostępna dla Ciebie. W tym artykule wyjaśniono zarówno obsługę etykietki narzędzi utworzonej przez Kreatora aplikacji, jak i sposób dodawania obsługi etykietek narzędzi do aplikacji.

Ten artykuł obejmuje:

- [Aktywowanie wskazówek dotyczących narzędzi](#_core_activating_tool_tips)

- [Aktualizacje paska stanu flyby](#_core_fly_by_status_bar_updates)

## <a name="activating-tool-tips"></a><a name="_core_activating_tool_tips"></a>Aktywowanie wskazówek dotyczących narzędzi

Aby aktywować wskazówki dotyczące narzędzi w aplikacji, należy wykonać dwie czynności:

- Dodaj styl CBRS_TOOLTIPS do innych stylów (takich jak WS_CHILD, WS_VISIBLE i inne style **CBRS_)** przekazany jako parametr *dwStyle* do [funkcji CToolBar::Create](../mfc/reference/ctoolbar-class.md#create) lub w [SetBarStyle](../mfc/reference/ccontrolbar-class.md#setbarstyle).

- Jak opisano w poniższej procedurze, należy dołączyć tekst końcówki paska narzędzi, oddzielony znakiem nowego wiersza ("\n"), do zasobu ciągu zawierającego wiersz wiersza polecenia dla polecenia paska narzędzi. Zasób ciągu współumieści identyfikator przycisku paska narzędzi.

#### <a name="to-add-the-tool-tip-text"></a>Aby dodać tekst etykietki narzędzia

1. Podczas edytowania paska narzędzi w edytorze paska narzędzi otwórz okno **Właściwości przycisku paska narzędzi** dla danego przycisku.

1. W polu **Monituj** tekst, który ma być wyświetlany w etykietce narzędzia dla tego przycisku.

> [!NOTE]
> Ustawienie tekstu jako właściwości przycisku w edytorze paska narzędzi zastępuje poprzednią procedurę, w której trzeba było otworzyć i edytować zasób ciągu.

Jeśli na pasku sterowania z włączonymi końcówkami narzędzi umieszczone są formanty podrzędne, na pasku sterowania zostanie wyświetlona wskazówka dla każdego formantu podrzędnego na pasku sterowania, o ile spełnia następujące kryteria:

- Identyfikator formantu nie jest - 1.

- Wpis tabeli ciągów o tym samym identyfikatorze co formant podrzędny w pliku zasobu ma ciąg poradki narzędzia.

## <a name="flyby-status-bar-updates"></a><a name="_core_fly_by_status_bar_updates"></a>Aktualizacje paska stanu flyby

Funkcją związaną z poradami narzędzi jest aktualizacja paska stanu "flyby". Domyślnie komunikat na pasku stanu opisuje tylko określony przycisk paska narzędzi, gdy przycisk jest aktywowany. Dołączając CBRS_FLYBY na liście stylów `CToolBar::Create`przekazanych do , możesz zaktualizować te komunikaty, gdy kursor myszy przechodzi przez pasek narzędzi bez faktycznego aktywowania przycisku.

### <a name="what-do-you-want-to-know-more-about"></a>Co chcesz wiedzieć więcej o

- [Implementacja paska narzędzi MFC (informacje ogólne dotyczące pasków narzędzi)](../mfc/mfc-toolbar-implementation.md)

- [Dokowanie i pływające paski narzędzi](../mfc/docking-and-floating-toolbars.md)

- Klasy [CToolBar](../mfc/reference/ctoolbar-class.md) i [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)

- [Praca z kontrolką paska narzędzi](../mfc/working-with-the-toolbar-control.md)

- [Korzystanie ze starych pasków narzędzi](../mfc/using-your-old-toolbars.md)

## <a name="see-also"></a>Zobacz też

[MFC, implementacja paska narzędzi](../mfc/mfc-toolbar-implementation.md)
