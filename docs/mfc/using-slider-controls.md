---
title: Używanie formantów suwaka | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CSliderCtrl class [MFC], using
- slider controls
- slider controls [MFC], using
ms.assetid: 2b1a8ac8-2b17-41e1-aa24-83c1fd737049
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9180d792f38652b22f430e497ef0e42dc54f6d73
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
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

