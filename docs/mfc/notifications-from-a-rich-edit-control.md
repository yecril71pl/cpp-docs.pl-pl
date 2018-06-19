---
title: Powiadomienia z zaawansowanej edycji kontrolki | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: c678af3444ef408a0a9c50e972942d67e2d3cf1b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33353856"
---
# <a name="notifications-from-a-rich-edit-control"></a>Powiadomienia z formantów edycji wzbogaconej
Powiadomień wiadomości zdarzenia mające wpływ na wzbogaconej formantów edycji raportu ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)). One mogą być przetwarzane przez okno nadrzędne lub za pomocą odbicia wiadomości przez zaawansowanej edycji kontrolki. Formanty edycji wzbogaconej obsługuje wszystkie komunikaty powiadomień używane z formantami edycji, a także kilka te dodatkowe. Można określić, które komunikaty powiadomień kontrolki zaawansowanej edycji wysyła jej okna nadrzędnego przez ustawienie jej "maski zdarzeń."  
  
 Aby ustawić maski zdarzeń dla formantów edycji wzbogaconej, użyj [SetEventMask](../mfc/reference/cricheditctrl-class.md#seteventmask) funkcję elementu członkowskiego. Można pobrać bieżącego maski zdarzeń dla formantu edycji wzbogaconej przy użyciu [GetEventMask](../mfc/reference/cricheditctrl-class.md#geteventmask) funkcję elementu członkowskiego.  
  
 Następuje listy kilka określone powiadomienia i ich zastosowań:  
  
-   **EN_MSGFILTER** Obsługa **EN_MSGFILTER** powiadomień umożliwia klasę, albo zaawansowanej edycji formantu lub jego okno nadrzędne, filtrować wszystkie klawiatury i myszy dane wejściowe do formantu. Program obsługi można zapobiec przetwarzanych wiadomości klawiatury lub myszy lub zmienić komunikat przez zmodyfikowanie określonego [MSGFILTER](http://msdn.microsoft.com/library/windows/desktop/bb787936) struktury.  
  
-   **EN_PROTECTED** obsługi **EN_PROTECTED** wiadomość z powiadomieniem do wykrycia, gdy użytkownik próbuje zmodyfikować chroniony tekst. Aby oznaczyć zakres tekstu jako chroniony, można ustawić efekt chronionych znaków. Aby uzyskać więcej informacji, zobacz [formatowanie znaków w formantach edycji wzbogaconej](../mfc/character-formatting-in-rich-edit-controls.md).  
  
-   **EN_DROPFILES** można włączyć użytkownika można usunąć pliki w formancie edycji wzbogaconej przez przetwarzanie **EN_DROPFILES** wiadomość z powiadomieniem. Określony [ENDROPFILES](http://msdn.microsoft.com/library/windows/desktop/bb787895) struktura zawiera informacje o plikach usuwane.  
  
-   **EN_SELCHANGE** aplikacji może wykryć, gdy bieżące zaznaczenie zostanie zmienione przez przetwarzanie **EN_SELCHANGE** wiadomość z powiadomieniem. Określa komunikat powiadomienia [selchange —](http://msdn.microsoft.com/library/windows/desktop/bb787952) struktury zawierającej informacje o nowe zaznaczenie.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CRichEditCtrl](../mfc/using-cricheditctrl.md)   
 [Kontrolki](../mfc/controls-mfc.md)

