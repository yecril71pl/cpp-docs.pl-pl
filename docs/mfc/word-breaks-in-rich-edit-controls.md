---
title: Podziały wyrazów w formantach edycji wzbogaconej
ms.date: 11/04/2016
helpviewer_keywords:
- CRichEditCtrl class [MFC], word breaks in
- word breaks
- breaking words in CRichEditCtrl
- rich edit controls [MFC], word breaks in
ms.assetid: 641dcf9e-7b40-4dc0-85f7-575a8c142f73
ms.openlocfilehash: efe4a0a2c06c14d913d43c51d1f0100f27c6a537
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50632599"
---
# <a name="word-breaks-in-rich-edit-controls"></a>Podziały wyrazów w formantach edycji wzbogaconej

Kontrolki edycji wzbogaconej ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) wywołuje funkcję o nazwie "word podziału procedury" Aby znaleźć przerwy między wyrazami i określić, gdzie może przerwać wierszy. Kontrolka używa tych informacji podczas wykonywania operacji zawijanie wyrazów i podczas przetwarzania kombinacji klawiszy CTRL + Strzałka w lewo i CTRL + Strzałka w prawo. Aplikacja może wysyłać komunikaty do kontrolki edycji wzbogaconej, aby zastąpić procedurę dzielenia wyrazów domyślne, można pobrać informacji o dzielenia wyrazów i określić, jakie wiersz dany znak, który znajduje się.

## <a name="see-also"></a>Zobacz też

[Korzystanie z CRichEditCtrl](../mfc/using-cricheditctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)

