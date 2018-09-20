---
title: Składniki okna dialogowego w strukturze | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC dialog boxes [MFC], creating
- dialog classes [MFC], dialog box components
- MFC dialog boxes [MFC], about MFC dialog boxes
- dialog templates [MFC], MFC framework
- MFC dialog boxes [MFC], dialog resource
ms.assetid: 592db160-0a8a-49be-ac72-ead278aca53f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9fb72e2961eec53b2dea8e37cfc39ccbcc0c5f27
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46397172"
---
# <a name="dialog-box-components-in-the-framework"></a>Składniki okna dialogowego w strukturze

W ramach MFC okno dialogowe ma dwa składniki:

- Zasób szablonu okna dialogowego, który określa formantów okna dialogowego i ich rozmieszczenie.

     Zasobu okna dialogowego przechowuje szablonu okna dialogowego, w którym Windows tworzy okno dialogowe i wyświetla je. Szablon służy do cechy okno dialogowe, w tym jego rozmiar, lokalizację, stylu i typy i położenie formantów w oknie dialogowym. Zazwyczaj używa się szablonu okna dialogowego przechowywana jako zasób, ale można też utworzyć własny szablon w pamięci.

- Pochodne klasy okien dialogowych [CDialog](../mfc/reference/cdialog-class.md)w celu zapewnienia interfejsu programowego zarządzania okno dialogowe.

     Okno dialogowe jest oknem i zostanie dołączony do okna Windows, gdy jest widoczne. Podczas tworzenia okna dialogowego, zasobu szablonu okna dialogowego służy jako szablon do tworzenia podrzędnego kontrolki okna dla okna dialogowego.

## <a name="see-also"></a>Zobacz też

[Okna dialogowe](../mfc/dialog-boxes.md)<br/>
[Cykl życiowy okna dialogowego](../mfc/life-cycle-of-a-dialog-box.md)

