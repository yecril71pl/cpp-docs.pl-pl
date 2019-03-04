---
title: Style formantu postępu
ms.date: 11/19/2018
helpviewer_keywords:
- PBS_SMOOTH style
- progress controls [MFC], styles
- PBS_VERTICAL style
- CProgressCtrl class [MFC], styles
ms.assetid: 39eb8081-bc20-4552-91b9-e7cdd1b7d8ae
ms.openlocfilehash: 3adbd32456b1375bd2dc8574220e083ca3d83ee9
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57296335"
---
# <a name="styles-for-the-progress-control"></a>Style formantu postępu

Podczas początkowego tworzenia formantu postępu ([CProgressCtrl::Create](../mfc/reference/cprogressctrl-class.md#create)), użyj *dwStyle* parametru, aby określić żądaną okna Style kontrolki postępu. Poniżej przedstawiono szczegółową listę style odpowiednie okna. Kontrolka ignoruje dowolny styl okna innych niż wymienione w tym miejscu. Formant należy zawsze tworzyć jako okna podrzędnego, zazwyczaj z elementem nadrzędnym okno dialogowe.

|Styl okna|Efekt|
|------------------|------------|
|WS_BORDER|Tworzy obramowania okna.|
|WS_CHILD|Tworzy okno podrzędne (zawsze należy używać w przypadku `CProgressCtrl`).|
|WS_CLIPCHILDREN|Wyklucza obszar zajmowany przez okna podrzędne Kiedy rysujesz w oknie nadrzędnym. Używany podczas tworzenia okna nadrzędnego.|
|WS_CLIPSIBLINGS|Przycina okien podrzędnych względem siebie.|
|WS_DISABLED|Tworzy okno, które jest początkowo wyłączone.|
|WS_VISIBLE|Tworzy okno, które jest początkowo widoczne.|
|WS_TABSTOP|Określa, że formant może odebrać fokus, gdy użytkownik naciśnie klawisz TAB aby przenieść do niego.|

Ponadto można określić dwa style, które mają zastosowanie tylko do formantu postępu pbs_vertical — i pbs_smooth —.

Pbs_vertical — umożliwia orientacja kontrolki w pionie, a nie w poziomie. Do wypełnienia kontrolki całkowicie, zamiast wyświetlić małe kwadraty nakreślonego, które wypełniają formant stopniowo, należy użyć pbs_smooth —.

Bez pbs_smooth — styl:

![Styl paska postępu standardowa](../mfc/media/vc4ruw1.gif "styl paska postępu standardowe")

Za pomocą pbs_smooth — i pbs_vertical — styl:

![Pasek stylu płynne i pionowy postępu](../mfc/media/vc4ruw2.gif "pasek stylu płynne i pionowy postępu")

Aby uzyskać więcej informacji, zobacz [Style okna ramowego](../mfc/reference/styles-used-by-mfc.md#frame-window-styles-mfc) w *odwołanie MFC*.

## <a name="see-also"></a>Zobacz także

[Korzystanie z CProgressCtrl](../mfc/using-cprogressctrl.md)
