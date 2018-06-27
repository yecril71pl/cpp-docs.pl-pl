---
title: Style formantu suwaka | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- slider controls [MFC], styles
- CSliderCtrl class [MFC], styles
- styles [MFC], CSliderCtrl
- styles [MFC], slider controls
ms.assetid: 64c491fc-5af1-4f97-ae30-854071b3dc02
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f76fbe9f85d978a5c2865b48720588b620508a07
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2018
ms.locfileid: "36951055"
---
# <a name="slider-control-styles"></a>Style formantu suwaka
Formanty suwaka ([CSliderCtrl](../mfc/reference/csliderctrl-class.md)) może mieć orientacji pionowej lub poziomej. Mogą oni mieć znaczniki osi po obu stronach obu stronach lub nie. One mogą służyć do określania zakresu kolejnych wartości. Te właściwości są określane za pomocą style formantu suwaka, które można określić podczas tworzenia suwaka.  
  
 Style TBS_HORZ i TBS_VERT określają Orientacja formantu suwaka. Jeśli nie określisz orientacji, suwak jest ustawiony w poziomie.  
  
 Styl TBS_AUTOTICKS tworzy formantu suwaka, który ma znacznik osi dla każdego kolejnego przyrostu wartości w swoim zakresie wartości. Te znaczniki są dodawane automatycznie podczas wywoływania [SetRange](../mfc/reference/csliderctrl-class.md#setrange) funkcję elementu członkowskiego. Jeśli nie określisz TBS_AUTOTICKS, możesz użyć funkcji elementu członkowskiego, takich jak [SetTic](../mfc/reference/csliderctrl-class.md#settic) i [SetTicFreq](../mfc/reference/csliderctrl-class.md#setticfreq), aby określić położenia znaczników. Aby utworzyć suwaka, które nie są wyświetlane znaczniki, można użyć stylu TBS_NOTICKS.  
  
 Znaczników można wyświetlać na jedną lub obie te strony suwaka. Dla kontrolki suwaka Poziomy można określić styl TBS_BOTTOM lub TBS_TOP. Dla formantów pionowej kontrolce slider można określić styl TBS_RIGHT lub TBS_LEFT. (TBS_BOTTOM i TBS_RIGHT są ustawienia domyślne). Znaczniki osi po obu stronach suwaka w dowolnym orientacji Określ styl TBS_BOTH.  
  
 Formant suwaka można wyświetlić wybranego zakresu, tylko wtedy, gdy Określ styl TBS_ENABLESELRANGE podczas jego tworzenia. Kontrolki suwaka po ten styl znaczników w pozycji datę początkową i końcową wybranego zakresu są wyświetlane jako trójkąty (zamiast kreski pionowej) i zostanie wyróżniona wybranego zakresu. Na przykład zaznaczanie zakresów mogą być przydatne w prostej aplikacji planowania. Użytkownik może wybrać zakres znaczników odpowiadający godzin w ciągu dnia, aby określić czas zaplanowanego spotkania.  
  
 Domyślnie długość suwaka formantu suwaka zmienia się jako zmiany zakresu zaznaczenia. Jeśli suwaka styl TBS_FIXEDLENGTH, długość suwak jest taka sama, nawet jeśli zmieni się wybranego zakresu. Suwaka, którego styl TBS_NOTHUMB nie obejmuje suwaka.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CSliderCtrl](../mfc/using-csliderctrl.md)   
 [Kontrolki](../mfc/controls-mfc.md)

