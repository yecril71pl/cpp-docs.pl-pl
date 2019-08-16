---
title: Powiadomienia z formantów edycji wzbogaconej
ms.date: 11/04/2016
helpviewer_keywords:
- messages [MFC], notification [MFC]
- CRichEditCtrl class [MFC], notifications
- rich edit controls [MFC], notifications
- notifications [MFC], from CRichEditCtrl
ms.assetid: eb5304fe-f4f3-4557-9ebf-3095dea383c4
ms.openlocfilehash: d097996e61a3d461dacd3d30e13b9262c7d32434
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508053"
---
# <a name="notifications-from-a-rich-edit-control"></a>Powiadomienia z formantów edycji wzbogaconej

Komunikaty powiadomień zdarzenia mające wpływ na kontrolkę edycji wzbogaconej ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)). Mogą być przetwarzane przez okno nadrzędne lub, przy użyciu odbicia komunikatu, przez samą kontrolkę edycji wzbogaconej. Kontrolki edycji wzbogaconej obsługują wszystkie komunikaty powiadomień używane z kontrolkami edycji, a także kilka dodatkowych. Możesz określić, które wiadomości z powiadomieniem formant edycji wzbogaconej wysyła jego okno nadrzędne, ustawiając jego "maskę zdarzeń".

Aby ustawić maskę zdarzeń dla kontrolki edycji wzbogaconej, użyj funkcji składowej [SetEventMask](../mfc/reference/cricheditctrl-class.md#seteventmask) . Można pobrać bieżącą maskę zdarzeń dla kontrolki edycji wzbogaconej przy użyciu funkcji składowej [GetEventMask —](../mfc/reference/cricheditctrl-class.md#geteventmask) .

W poniższych akapitach wymieniono kilka konkretnych powiadomień i ich zastosowania:

- EN_MSGFILTER Obsługa powiadomień EN_MSGFILTER umożliwia klasy, kontrolki edycji wzbogaconej lub jej okna nadrzędnego, filtrowanie wszystkich danych wejściowych klawiatury i myszy do kontrolki. Program obsługi może zapobiec przetwarzaniu lub przetworzeniu komunikatu z klawiatury lub myszy albo zmienić komunikat, modyfikując określoną strukturę [MSGFILTER](/windows/win32/api/richedit/ns-richedit-msgfilter) .

- EN_PROTECTED obsługiwać komunikat powiadomienia EN_PROTECTED w celu wykrycia, kiedy użytkownik próbuje zmodyfikować chroniony tekst. Aby oznaczyć zakres tekstu jako chroniony, można ustawić efekt chronionego znaku. Aby uzyskać więcej informacji, zobacz [Formatowanie znaków w formantach edycji wzbogaconej](../mfc/character-formatting-in-rich-edit-controls.md).

- EN_DROPFILES można umożliwić użytkownikowi upuszczanie plików w kontrolce edycji wzbogaconej, przetwarzając komunikat z powiadomieniem EN_DROPFILES. Określona struktura [ENDROPFILES](/windows/win32/api/richedit/ns-richedit-endropfiles) zawiera informacje o usuwanych plikach.

- EN_SELCHANGE aplikacja może wykryć, kiedy bieżące zaznaczenie zostanie zmienione przez przetworzenie komunikatu powiadomienia EN_SELCHANGE. Komunikat powiadomienia określa strukturę [SELCHANGE](/windows/win32/api/richedit/ns-richedit-selchange) zawierającą informacje o nowym zaznaczeniu.

## <a name="see-also"></a>Zobacz także

[Korzystanie z CRichEditCtrl](../mfc/using-cricheditctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)
