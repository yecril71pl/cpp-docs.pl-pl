---
title: Powiadomienia z rozbudowanego formantów edycji | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- messages [MFC], notification [MFC]
- CRichEditCtrl class [MFC], notifications
- rich edit controls [MFC], notifications
- notifications [MFC], from CRichEditCtrl
ms.assetid: eb5304fe-f4f3-4557-9ebf-3095dea383c4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a64abf4312460384ddfa78fa2220cfb88bf664c7
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43195074"
---
# <a name="notifications-from-a-rich-edit-control"></a>Powiadomienia z formantów edycji wzbogaconej
Komunikaty powiadomień zdarzeń mających wpływ na zaawansowane formant edycji raportu ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)). One mogą być przetwarzane przez okno nadrzędne lub przy użyciu odbicia komunikatu przez zaawansowanych Edytuj kontrolkę. Kontrolki edycji wzbogaconej obsługuje wszystkie komunikaty powiadomień używane z formantami edycji wzbogaconej także kilka dodatkowych. Można określić, które komunikaty powiadomień kontrolki edycji wzbogaconej wysyła okna nadrzędnego, ustawiając jego "maski zdarzeń."  
  
 Aby ustawić maski zdarzeń dla formantu edycji wzbogaconej, użyj [seteventmask —](../mfc/reference/cricheditctrl-class.md#seteventmask) funkcja elementu członkowskiego. Można pobrać bieżącego maski zdarzeń dla formantu edycji wzbogaconej przy użyciu [geteventmask —](../mfc/reference/cricheditctrl-class.md#geteventmask) funkcja elementu członkowskiego.  
  
 Następuje lista kilka określone powiadomienia i ich zastosowań:  
  
-   EN_MSGFILTER Obsługa powiadomienia EN_MSGFILTER umożliwia klasy, albo formantu bogatej edycji lub okna nadrzędnego, filtrować wszystkie klawiatury i myszy do formantu. Program obsługi może uniemożliwić przetwarzanego komunikatu klawiatury lub myszy lub zmienić modyfikując określony komunikat [MSGFILTER](/windows/desktop/api/richedit/ns-richedit-_msgfilter) struktury.  
  
-   EN_PROTECTED obsługi komunikatu powiadomienia EN_PROTECTED, aby wykryć, kiedy użytkownik próbuje zmodyfikować chroniony plik tekstowy. Aby oznaczyć zakres tekstu jako chroniony, można ustawić efekt chronionych znaków. Aby uzyskać więcej informacji, zobacz [formatowanie znaków w formantach edycji wzbogaconej](../mfc/character-formatting-in-rich-edit-controls.md).  
  
-   EN_DROPFILES umożliwiają użytkownikowi umieszczają pliki w formancie edycji wzbogaconej przez przetwarzanie komunikatów powiadomień EN_DROPFILES. Określony [ENDROPFILES](/windows/desktop/api/richedit/ns-richedit-_endropfiles) struktura zawiera informacje o plikach porzucana.  
  
-   EN_SELCHANGE aplikacji może wykryć, gdy bieżące zaznaczenie zostanie zmienione przez przetwarzanie komunikatów powiadomień EN_SELCHANGE. Określa komunikat powiadomienia [selchange —](/windows/desktop/api/richedit/ns-richedit-_selchange) struktury zawierającej informacje o nowe zaznaczenie.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CRichEditCtrl](../mfc/using-cricheditctrl.md)   
 [Kontrolki](../mfc/controls-mfc.md)

