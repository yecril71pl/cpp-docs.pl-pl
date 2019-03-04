---
title: Składniki okna dialogowego w strukturze
ms.date: 11/04/2016
helpviewer_keywords:
- MFC dialog boxes [MFC], creating
- dialog classes [MFC], dialog box components
- MFC dialog boxes [MFC], about MFC dialog boxes
- dialog templates [MFC], MFC framework
- MFC dialog boxes [MFC], dialog resource
ms.assetid: 592db160-0a8a-49be-ac72-ead278aca53f
ms.openlocfilehash: 88027df7433267925e91db2d368b744cee8a9e75
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57262743"
---
# <a name="dialog-box-components-in-the-framework"></a>Składniki okna dialogowego w strukturze

W ramach MFC okno dialogowe ma dwa składniki:

- Zasób szablonu okna dialogowego, który określa formantów okna dialogowego i ich rozmieszczenie.

   Zasobu okna dialogowego przechowuje szablonu okna dialogowego, w którym Windows tworzy okno dialogowe i wyświetla je. Szablon służy do cechy okno dialogowe, w tym jego rozmiar, lokalizację, stylu i typy i położenie formantów w oknie dialogowym. Zazwyczaj używa się szablonu okna dialogowego przechowywana jako zasób, ale można też utworzyć własny szablon w pamięci.

- Pochodne klasy okien dialogowych [CDialog](../mfc/reference/cdialog-class.md)w celu zapewnienia interfejsu programowego zarządzania okno dialogowe.

   Okno dialogowe jest oknem i zostanie dołączony do okna Windows, gdy jest widoczne. Podczas tworzenia okna dialogowego, zasobu szablonu okna dialogowego służy jako szablon do tworzenia podrzędnego kontrolki okna dla okna dialogowego.

## <a name="see-also"></a>Zobacz także

[Okna dialogowe](../mfc/dialog-boxes.md)<br/>
[Cykl życiowy okna dialogowego](../mfc/life-cycle-of-a-dialog-box.md)
