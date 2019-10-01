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
ms.openlocfilehash: 15d01924be811a9c9ec8ea333870f444bf9aa61a
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685835"
---
# <a name="dialog-box-components-in-the-framework"></a>Składniki okna dialogowego w strukturze

W strukturze MFC okno dialogowe ma dwa składniki:

- Zasób szablonu okna dialogowego, który określa kontrolki okna dialogowego i ich położenie.

   Zasób okna dialogowego przechowuje szablon okna dialogowego, z którego system Windows tworzy okno dialogowe i wyświetla je. Szablon określa charakterystyki okna dialogowego, w tym jego rozmiar, lokalizację, styl oraz typy i położenia kontrolek okna dialogowego. Zwykle używany jest szablon okna dialogowego przechowywany jako zasób, ale można również utworzyć własny szablon w pamięci.

- Klasa okna dialogowego, która pochodzi od [CDialog](../mfc/reference/cdialog-class.md), aby zapewnić interfejs programistyczny do zarządzania oknem dialogowym.

   Okno dialogowe jest oknem i zostanie dołączone do okna systemu Windows, gdy będzie widoczne. Po utworzeniu okna dialogowego zasób szablonu okna dialogowego jest używany jako szablon do tworzenia kontrolek okna podrzędnego dla okna dialogowego.

## <a name="see-also"></a>Zobacz także

[Okna dialogowe](../mfc/dialog-boxes.md)<br/>
[Praca z polami okna dialogowego w MFC](../mfc/life-cycle-of-a-dialog-box.md)
