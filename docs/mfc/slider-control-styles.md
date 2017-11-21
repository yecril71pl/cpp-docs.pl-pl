---
title: Style formantu suwaka | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- slider controls [MFC], styles
- CSliderCtrl class [MFC], styles
- styles [MFC], CSliderCtrl
- styles [MFC], slider controls
ms.assetid: 64c491fc-5af1-4f97-ae30-854071b3dc02
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 43d8cf7ae406f2d29a381f765686e6537243de3f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="slider-control-styles"></a>Style formantu suwaka
Formanty suwaka ([CSliderCtrl](../mfc/reference/csliderctrl-class.md)) może mieć orientacji pionowej lub poziomej. Mogą oni mieć znaczniki osi po obu stronach obu stronach lub nie. One mogą służyć do określania zakresu kolejnych wartości. Te właściwości są określane za pomocą style formantu suwaka, które można określić podczas tworzenia suwaka.  
  
 `TBS_HORZ` i `TBS_VERT` style określić orientację przestrzenną kontrolki suwaka. Jeśli nie określisz orientacji, suwak jest ustawiony w poziomie.  
  
 `TBS_AUTOTICKS` Styl tworzy formantu suwaka, który ma znacznik osi dla każdego kolejnego przyrostu wartości w swoim zakresie wartości. Te znaczniki są dodawane automatycznie podczas wywoływania [SetRange](../mfc/reference/csliderctrl-class.md#setrange) funkcję elementu członkowskiego. Jeśli nie określisz `TBS_AUTOTICKS`, można użyć funkcji elementów członkowskich, takich jak [SetTic](../mfc/reference/csliderctrl-class.md#settic) i [SetTicFreq](../mfc/reference/csliderctrl-class.md#setticfreq), aby określić położenia znaczników. Aby utworzyć suwaka, które nie są wyświetlane znaczniki, można użyć `TBS_NOTICKS` stylu.  
  
 Znaczników można wyświetlać na jedną lub obie te strony suwaka. Można określić dla kontrolki suwaka poziomy `TBS_BOTTOM` lub `TBS_TOP` styl. Można określić dla kontrolki suwaka pionowego, `TBS_RIGHT` lub `TBS_LEFT` styl. (`TBS_BOTTOM` i `TBS_RIGHT` są ustawienia domyślne.) Znaczniki osi po obu stronach suwaka w dowolnym orientacji, można określić `TBS_BOTH` stylu.  
  
 Formantu suwaka można wyświetlić wybranego zakresu, tylko jeśli określisz `TBS_ENABLESELRANGE` stylów podczas jego tworzenia. Kontrolki suwaka po ten styl znaczników w pozycji datę początkową i końcową wybranego zakresu są wyświetlane jako trójkąty (zamiast kreski pionowej) i zostanie wyróżniona wybranego zakresu. Na przykład zaznaczanie zakresów mogą być przydatne w prostej aplikacji planowania. Użytkownik może wybrać zakres znaczników odpowiadający godzin w ciągu dnia, aby określić czas zaplanowanego spotkania.  
  
 Domyślnie długość suwaka formantu suwaka zmienia się jako zmiany zakresu zaznaczenia. Jeśli ma suwaka **TBS_FIXEDLENGTH** stylu, długość suwak jest taka sama, nawet jeśli zmieni się wybranego zakresu. Formantu suwaka, który ma **TBS_NOTHUMB** style nie ma suwaka.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CSliderCtrl](../mfc/using-csliderctrl.md)   
 [Formanty](../mfc/controls-mfc.md)

