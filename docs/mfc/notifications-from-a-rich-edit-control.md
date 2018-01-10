---
title: Powiadomienia z zaawansowanej edycji kontrolki | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- messages [MFC], notification [MFC]
- CRichEditCtrl class [MFC], notifications
- rich edit controls [MFC], notifications
- notifications [MFC], from CRichEditCtrl
ms.assetid: eb5304fe-f4f3-4557-9ebf-3095dea383c4
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: fcfcb2e4fe333db1ed629489b405255d4ab050b9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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

