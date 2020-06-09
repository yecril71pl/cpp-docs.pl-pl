---
title: Tworzenie obiektu CToolBarCtrl
ms.date: 11/04/2016
helpviewer_keywords:
- toolbar controls [MFC], creating
- CToolBarCtrl class [MFC], creating toolbars
ms.assetid: a4f6bf0c-0195-4dbf-a09e-aee503e19dc3
ms.openlocfilehash: 2627f9aaceeab7760e15b23435233e124c5ea6f0
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619003"
---
# <a name="creating-a-ctoolbarctrl-object"></a>Tworzenie obiektu CToolBarCtrl

Obiekty [CToolBarCtrl](reference/ctoolbarctrl-class.md) zawierają kilka wewnętrznych struktur danych — listę map bitowych obrazów przycisków, listę ciągów etykiet przycisków i listę `TBBUTTON` struktur, które kojarzą obraz i/lub ciąg z pozycją, stylem, STANem i identyfikatorem polecenia przycisku. Każdy element tych struktur danych jest określany przez indeks (liczony od zera). Aby można było użyć `CToolBarCtrl` obiektu, należy skonfigurować te struktury danych. Aby uzyskać listę struktur danych, zobacz [kontrolki paska narzędzi](controls-mfc.md) w Windows SDK. Lista ciągów może być używana tylko dla etykiet przycisków; nie można pobrać ciągów z paska narzędzi.

Aby użyć `CToolBarCtrl` obiektu, zwykle wykonaj następujące kroki:

### <a name="to-use-a-ctoolbarctrl-object"></a>Aby użyć obiektu CToolBarCtrl

1. Utwórz obiekt [CToolBarCtrl](reference/ctoolbarctrl-class.md) .

1. Wywołanie [Create](reference/ctoolbarctrl-class.md#create) , aby utworzyć formant wspólny paska narzędzi systemu Windows i dołączyć go do `CToolBarCtrl` obiektu. Jeśli chcesz, aby obrazy mapy bitowej przycisków, Dodaj mapy bitowe przycisków na pasku narzędzi, wywołując metodę [Addmap bitowych](reference/ctoolbarctrl-class.md#addbitmap). Jeśli potrzebujesz etykiet ciągów dla przycisków, Dodaj ciągi do paska narzędzi, wywołując [AddString](reference/ctoolbarctrl-class.md#addstring) i/lub [AddStrings](reference/ctoolbarctrl-class.md#addstrings). Po wywołaniu `AddString` i/lub `AddStrings` , należy wywołać [AutoSize](reference/ctoolbarctrl-class.md#autosize) w celu uzyskania ciągu lub ciągów do wyświetlenia.

1. Dodaj struktury przycisków do paska narzędzi, wywołując [AddButtons](reference/ctoolbarctrl-class.md#addbuttons).

1. Aby uzyskać wskazówki dotyczące narzędzi, należy obsłużyć **TTN_NEEDTEXT** komunikatów w oknie właściciela paska narzędzi, zgodnie z opisem w temacie [Obsługa powiadomień etykietki narzędzia](handling-tool-tip-notifications.md).

1. Jeśli chcesz, aby użytkownik mógł dostosować ten pasek narzędzi, obsługuj komunikaty powiadomień o dostosowywaniu w oknie właściciela zgodnie z opisem w temacie [Obsługa powiadomień dotyczących dostosowywania](handling-customization-notifications.md).

## <a name="see-also"></a>Zobacz też

[Korzystanie z CToolBarCtrl](using-ctoolbarctrl.md)<br/>
[Formanty](controls-mfc.md)
