---
title: Style formantu postępu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- PBS_SMOOTH style
- progress controls [MFC], styles
- PBS_VERTICAL style
- CProgressCtrl class [MFC], styles
ms.assetid: 39eb8081-bc20-4552-91b9-e7cdd1b7d8ae
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ce520991b078f01e0551661516bfe7f24c53cf46
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46442919"
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

![Styl paska postępu standardowa](../mfc/media/vc4ruw1.gif "vc4ruw1")

Za pomocą pbs_smooth — i pbs_vertical — styl:

![Pasek stylu płynne i pionowy postępu](../mfc/media/vc4ruw2.gif "vc4ruw2")

Aby uzyskać więcej informacji, zobacz [Style okna ramowego](../mfc/reference/styles-used-by-mfc.md#frame-window-styles-mfc) w *odwołanie MFC*.

## <a name="see-also"></a>Zobacz też

[Korzystanie z CProgressCtrl](../mfc/using-cprogressctrl.md)

