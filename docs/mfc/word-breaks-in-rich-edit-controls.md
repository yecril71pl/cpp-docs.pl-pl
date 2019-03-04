---
title: Podziały wyrazów w formantach edycji wzbogaconej
ms.date: 11/04/2016
helpviewer_keywords:
- CRichEditCtrl class [MFC], word breaks in
- word breaks
- breaking words in CRichEditCtrl
- rich edit controls [MFC], word breaks in
ms.assetid: 641dcf9e-7b40-4dc0-85f7-575a8c142f73
ms.openlocfilehash: e71643350ced5b8ecff7c8ac7829741cc3e8493b
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57291187"
---
# <a name="word-breaks-in-rich-edit-controls"></a>Podziały wyrazów w formantach edycji wzbogaconej

Kontrolki edycji wzbogaconej ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) wywołuje funkcję o nazwie "word podziału procedury" Aby znaleźć przerwy między wyrazami i określić, gdzie może przerwać wierszy. Kontrolka używa tych informacji podczas wykonywania operacji zawijanie wyrazów i podczas przetwarzania kombinacji klawiszy CTRL + Strzałka w lewo i CTRL + Strzałka w prawo. Aplikacja może wysyłać komunikaty do kontrolki edycji wzbogaconej, aby zastąpić procedurę dzielenia wyrazów domyślne, można pobrać informacji o dzielenia wyrazów i określić, jakie wiersz dany znak, który znajduje się.

## <a name="see-also"></a>Zobacz także

[Korzystanie z CRichEditCtrl](../mfc/using-cricheditctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)
