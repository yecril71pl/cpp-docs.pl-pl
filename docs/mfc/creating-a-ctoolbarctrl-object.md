---
title: Tworzenie obiektu CToolBarCtrl
ms.date: 11/04/2016
f1_keywords:
- CToolBarCtrl
helpviewer_keywords:
- toolbar controls [MFC], creating
- CToolBarCtrl class [MFC], creating toolbars
ms.assetid: a4f6bf0c-0195-4dbf-a09e-aee503e19dc3
ms.openlocfilehash: ad75f346e21262b894d01efd351e6bb0a3ede3a1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50564674"
---
# <a name="creating-a-ctoolbarctrl-object"></a>Tworzenie obiektu CToolBarCtrl

[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) obiekty zawierają kilka wewnętrznych struktur danych — lista mapy bitowe przycisków obrazu, listę ciągów Etykieta przycisku i listę `TBBUTTON` struktur — która Skojarz obraz i/lub ciąg pozycji, style, stan, i Identyfikator polecenia przycisku. Każdy z elementów te struktury danych jest określany przez liczony od zera indeks. Przed użyciem `CToolBarCtrl` obiektu, należy skonfigurować te struktury danych. Aby uzyskać listę struktur danych, zobacz [kontrolki paska narzędzi](controls-mfc.md) w zestawie Windows SDK. Lista ciągów należy używać tylko dla etykiet przycisku. Nie można pobrać ciągów, na pasku narzędzi.

Aby użyć `CToolBarCtrl` obiektu będzie najczęściej wykonaj następujące kroki:

### <a name="to-use-a-ctoolbarctrl-object"></a>Aby użyć obiektu CToolBarCtrl

1. Konstruowania [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) obiektu.

1. Wywołaj [Utwórz](../mfc/reference/ctoolbarctrl-class.md#create) do tworzenia formantu typowego paska narzędzi Windows i dołącz je do `CToolBarCtrl` obiektu. Obrazy mapy bitowej dla przycisków, dodać mapy bitowe przycisków do paska narzędzi, wywołując [AddBitmap](../mfc/reference/ctoolbarctrl-class.md#addbitmap). Ciąg znaków etykiety dla przycisków, dodać ciągi do paska narzędzi, wywołując [addstring —](../mfc/reference/ctoolbarctrl-class.md#addstring) i/lub [AddStrings](../mfc/reference/ctoolbarctrl-class.md#addstrings). Po wywołaniu `AddString` i/lub `AddStrings`, należy wywołać [AutoSize](../mfc/reference/ctoolbarctrl-class.md#autosize) Aby uzyskać ciąg znaków lub ciągów są wyświetlane.

1. Dodaj struktur przycisk do paska narzędzi, wywołując [AddButtons](../mfc/reference/ctoolbarctrl-class.md#addbuttons).

1. Jeśli chcesz etykietek narzędzi, obsługi **TTN_NEEDTEXT** wiadomości w pasku narzędzi okna właściciela, zgodnie z opisem w [Obsługa powiadomień dotyczących Porada narzędzi](../mfc/handling-tool-tip-notifications.md).

1. Jeśli chcesz, aby użytkownika, aby mieć możliwość dostosowania na pasku narzędzi, obsługi dostosowywania komunikatów powiadomień w okno właściciela, zgodnie z opisem w [Obsługa powiadomień dotyczących dostosowania](../mfc/handling-customization-notifications.md).

## <a name="see-also"></a>Zobacz też

[Korzystanie z CToolBarCtrl](../mfc/using-ctoolbarctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)

