---
title: Operacje strumieniowe w formantach edycji wzbogaconej
ms.date: 11/04/2016
helpviewer_keywords:
- CRichEditCtrl class [MFC], stream operations
- CRichEditCtrl class [MFC], stream storage
- rich edit controls [MFC], stream operations
- storage, stream in CRichEditCtrl
- stream operations in CRichEditCtrl
- stream storage and CRichEditCtrl
ms.assetid: 110b4684-1e76-4ca6-9ef0-5bc8b2d93c78
ms.openlocfilehash: 73277f59dc0ad4dfe21d481d0b893903ed407ea9
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69512944"
---
# <a name="stream-operations-in-rich-edit-controls"></a>Operacje strumieniowe w formantach edycji wzbogaconej

Strumienie służą do transferowania danych do lub z kontrolki edycji wzbogaconej ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)). Strumień jest zdefiniowany przez strukturę [EDITSTREAM](/windows/win32/api/richedit/ns-richedit-editstream) , która określa bufor i funkcję wywołania zwrotnego zdefiniowanego przez aplikację.

Aby odczytać dane do kontrolki edycji wzbogaconej (czyli strumieniowego przesyłania danych w programie), użyj funkcji elementu członkowskiego [strumienia](../mfc/reference/cricheditctrl-class.md#streamin) . Kontrolka wielokrotnie wywołuje funkcję wywołania zwrotnego zdefiniowaną przez aplikację, która przenosi część danych do bufora za każdym razem.

Aby zapisać zawartość kontrolki edycji wzbogaconej (czyli strumieniowego przesyłania danych), można użyć funkcji składowej [StreamOut](../mfc/reference/cricheditctrl-class.md#streamout) . Kontrolka wielokrotnie zapisuje dane w buforze, a następnie wywołuje funkcję wywołania zwrotnego zdefiniowanego przez aplikację. Dla każdego wywołania funkcja wywołania zwrotnego zapisuje zawartość bufora.

## <a name="see-also"></a>Zobacz także

[Korzystanie z CRichEditCtrl](../mfc/using-cricheditctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)
