---
title: Tworzenie obiektu CToolBarCtrl
ms.date: 11/04/2016
helpviewer_keywords:
- toolbar controls [MFC], creating
- CToolBarCtrl class [MFC], creating toolbars
ms.assetid: a4f6bf0c-0195-4dbf-a09e-aee503e19dc3
ms.openlocfilehash: cf1d2eeb9efd2f8a1e7b433c0e18dd868a8b9aca
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79445894"
---
# <a name="creating-a-ctoolbarctrl-object"></a>Tworzenie obiektu CToolBarCtrl

Obiekty [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) zawierają kilka wewnętrznych struktur danych — listę map bitowych obrazów przycisków, listę ciągów etykiet przycisków i listę struktur `TBBUTTON` — które kojarzą obraz i/lub ciąg z pozycją, stylem, stanem i identyfikatorem polecenia przycisku. Każdy element tych struktur danych jest określany przez indeks (liczony od zera). Aby można było użyć obiektu `CToolBarCtrl`, należy skonfigurować te struktury danych. Aby uzyskać listę struktur danych, zobacz [kontrolki paska narzędzi](controls-mfc.md) w Windows SDK. Lista ciągów może być używana tylko dla etykiet przycisków; nie można pobrać ciągów z paska narzędzi.

Aby użyć obiektu `CToolBarCtrl`, należy zwykle wykonać następujące czynności:

### <a name="to-use-a-ctoolbarctrl-object"></a>Aby użyć obiektu CToolBarCtrl

1. Utwórz obiekt [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) .

1. [Utwórz wywołanie Create](../mfc/reference/ctoolbarctrl-class.md#create) , aby utworzyć formant wspólny paska narzędzi systemu Windows i dołączyć go do obiektu `CToolBarCtrl`. Jeśli chcesz, aby obrazy mapy bitowej przycisków, Dodaj mapy bitowe przycisków na pasku narzędzi, wywołując metodę [Addmap bitowych](../mfc/reference/ctoolbarctrl-class.md#addbitmap). Jeśli potrzebujesz etykiet ciągów dla przycisków, Dodaj ciągi do paska narzędzi, wywołując [AddString](../mfc/reference/ctoolbarctrl-class.md#addstring) i/lub [AddStrings](../mfc/reference/ctoolbarctrl-class.md#addstrings). Po wywołaniu `AddString` i/lub `AddStrings`, należy wywołać [AutoSize](../mfc/reference/ctoolbarctrl-class.md#autosize) w celu uzyskania ciągu lub ciągów do wyświetlenia.

1. Dodaj struktury przycisków do paska narzędzi, wywołując [AddButtons](../mfc/reference/ctoolbarctrl-class.md#addbuttons).

1. Aby uzyskać wskazówki dotyczące narzędzi, należy obsłużyć **TTN_NEEDTEXT** komunikatów w oknie właściciela paska narzędzi, zgodnie z opisem w temacie [Obsługa powiadomień etykietki narzędzia](../mfc/handling-tool-tip-notifications.md).

1. Jeśli chcesz, aby użytkownik mógł dostosować ten pasek narzędzi, obsługuj komunikaty powiadomień o dostosowywaniu w oknie właściciela zgodnie z opisem w temacie [Obsługa powiadomień dotyczących dostosowywania](../mfc/handling-customization-notifications.md).

## <a name="see-also"></a>Zobacz też

[Korzystanie z CToolBarCtrl](../mfc/using-ctoolbarctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)
