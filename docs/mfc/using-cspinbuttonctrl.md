---
title: Korzystanie z CSpinButtonCtrl | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CSpinButtonCtrl
dev_langs:
- C++
helpviewer_keywords:
- up-down controls [MFC], spin button control
- up-down controls
- spin button control
- CSpinButtonCtrl class [MFC], using
ms.assetid: a91db36b-e11e-42ef-8e89-51915cc486d2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bea2f2f51ed3b012ee9b5afe2572b2a6be9e0d57
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2018
ms.locfileid: "36955485"
---
# <a name="using-cspinbuttonctrl"></a>Korzystanie z CSpinButtonCtrl
*Pokrętła* formantu (znanej także jako *góra dół* kontroli) zawiera pary strzałki, które użytkownik może kliknąć, aby dostosować wartość. Ta wartość jest znana jako *bieżącego położenia*. Pozycja pozostaje w zakresie przycisku pokrętła. Gdy użytkownik kliknie strzałkę w górę, pozycja jest przesuwany maksymalną; a kiedy użytkownik kliknie strzałkę w dół, pozycja jest przesuwany minimum.  
  
 Kontrolka przycisku pokrętła jest reprezentowana w MFC przez [CSpinButtonCtrl](../mfc/reference/cspinbuttonctrl-class.md) klasy.  
  
> [!NOTE]
>  Domyślnie zakresu dla przycisku pokrętła ma maksymalną wartość zero (0) i minimalna wartość 100. Ponieważ wartość maksymalna jest mniejsza niż wartość minimalna, klikając strzałkę w górę zmniejsza położenie i kliknij strzałkę w dół zwiększa go. Użyj [CSpinButtonCtrl::SetRange](../mfc/reference/cspinbuttonctrl-class.md#setrange) dostosowanie tych wartości.  
  
 Zazwyczaj bieżące położenie jest wyświetlany w formancie pomocnika. Formant pomocnika nosi nazwę *zaprzyjaźnione okno*. Ilustracja kontrolki przycisku pokrętła, zobacz [o Up-Down — formanty](http://msdn.microsoft.com/library/windows/desktop/bb759889) w zestawie Windows SDK.  
  
 Aby utworzyć pokrętła i zaprzyjaźnione okno kontrolki edycji w programie Visual Studio, najpierw przeciągnij formant edycyjny do okna dialogowego lub okna, a następnie przeciągnij formant pokrętła. Wybierz kontrolki pokrętła i ustaw jej **automatyczne Zaprzyjaźnianie** i **Ustaw Buddy Integer** właściwości **True**. Również ustawić **wyrównanie** właściwości; **Wyrównaj do prawej** jest najbardziej typowych. Przy użyciu tych ustawień kontrolki edycji jest ustawiony jako okna zaprzyjaźnionego, ponieważ bezpośrednio poprzedza kontrolki edycji w kolejności tabulacji. Kontrolka edycji wyświetli liczb całkowitych i kontrolki pokrętła jest osadzony w prawej części kontrolki edycji. Opcjonalnie, należy określić prawidłowy zakres kontrolki pokrętła przy użyciu [CSpinButtonCtrl::SetRange](../mfc/reference/cspinbuttonctrl-class.md#setrange) metody. Nie obsługi zdarzeń są niezbędne do komunikacji między pokrętła i zaprzyjaźnione okno, ponieważ ich wymiany danych bezpośrednio. Użycie pokrętła do niektórych innych celów, na przykład strony przez system windows lub w oknach dialogowych, następnie dodaj obsługę wiadomości UDN_DELTAPOS i wykonać akcji niestandardowej.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o  
  
-   [Style przycisku pokrętła](../mfc/spin-button-styles.md)  
  
-   [Funkcje składowe przycisku pokrętła](../mfc/spin-button-member-functions.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Kontrolki](../mfc/controls-mfc.md)

