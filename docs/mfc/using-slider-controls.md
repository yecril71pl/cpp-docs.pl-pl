---
title: "Używanie formantów suwaka | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- CSliderCtrl class [MFC], using
- slider controls
- slider controls [MFC], using
ms.assetid: 2b1a8ac8-2b17-41e1-aa24-83c1fd737049
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4fdab6a7fae25845da81ee7263e045e50951f557
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="using-slider-controls"></a>Używanie formantów suwaka
Typowy sposób suwaka jest zgodny ze wzorcem poniżej:  
  
-   Formant nie zostanie utworzony. Jeśli formant jest określona w szablonie — okno dialogowe, tworzenie odbywa się automatycznie po utworzeniu okna dialogowego. (Powinien mieć [CSliderCtrl](../mfc/reference/csliderctrl-class.md) element członkowski w klasy okien dialogowych umożliwiająca suwaka.) Alternatywnie można użyć [Utwórz](../mfc/reference/csliderctrl-class.md#create) funkcji członkowskiej można utworzyć formantu jako okna podrzędnego każdego okna.  
  
-   Wywołanie różnych funkcji członkowskich zestawu, aby ustawić wartości dla formantu. Zmiany, które można wprowadzić obejmują ustawienie pozycji minimalną i maksymalną dla suwaka, rysowania znaczniki ustawienie wybranego zakresu i położenia suwaka. W przypadku kontrolek w oknie dialogowym jest odpowiedni moment, aby to zrobić, w oknie dialogowym [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog) funkcji.  
  
-   Gdy użytkownik rozpocznie się za pomocą formantu, wysyła komunikaty powiadomień dotyczących różnych. Można wyodrębnić wartość suwaka z formantu przez wywołanie metody [GetPos](../mfc/reference/csliderctrl-class.md#getpos) funkcję elementu członkowskiego.  
  
-   Gdy wszystko będzie gotowe za pomocą formantu, musisz upewnij się, że poprawnie zostanie zniszczony. W oknie dialogowym, jeśli kontrolka suwaka go i `CSliderCtrl` obiektu zostaną automatycznie usunięte. Jeśli nie, musisz upewnij się, że oba formantu i `CSliderCtrl` obiektu prawidłowo zostaną zniszczone.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CSliderCtrl](../mfc/using-csliderctrl.md)   
 [Kontrolki](../mfc/controls-mfc.md)

