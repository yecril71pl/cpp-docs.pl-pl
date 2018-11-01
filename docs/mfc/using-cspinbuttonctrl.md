---
title: Korzystanie z CSpinButtonCtrl
ms.date: 11/04/2016
f1_keywords:
- CSpinButtonCtrl
helpviewer_keywords:
- up-down controls [MFC], spin button control
- up-down controls
- spin button control
- CSpinButtonCtrl class [MFC], using
ms.assetid: a91db36b-e11e-42ef-8e89-51915cc486d2
ms.openlocfilehash: d3fe77c4d6d6b7bbea6e2b5f28954df4eec454d0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50545876"
---
# <a name="using-cspinbuttonctrl"></a>Korzystanie z CSpinButtonCtrl

*Przycisku pokrętła* kontroli (znany także jako *góra dół* kontroli) zawiera parę strzałki, które użytkownik może kliknąć, aby dopasować wartość. Ta wartość jest znana jako *bieżącej pozycji*. Pozycja nie wyjdzie poza zakres przycisku pokrętła. Gdy użytkownik kliknie strzałkę w górę, pozycja jest przesuwany maksymalną; a gdy użytkownik kliknie strzałkę w dół, pozycja jest przesuwany minimum.

Kontrolka przycisku pokrętła jest reprezentowana w MFC, [CSpinButtonCtrl](../mfc/reference/cspinbuttonctrl-class.md) klasy.

> [!NOTE]
>  Domyślnie zakres dla przycisku pokrętła ma maksymalną wartość zero (0) i co najmniej równa 100. Ponieważ wartość maksymalna jest mniejsza niż wartość minimalna, klikając strzałkę w górę zmniejsza pozycję i klikając strzałkę w dół jej zwiększenie. Użyj [CSpinButtonCtrl::SetRange](../mfc/reference/cspinbuttonctrl-class.md#setrange) dostosować te wartości.

Zazwyczaj bieżące położenie jest wyświetlany w kontrolce pomocnika. Kontrolka pomocnika jest znany jako *okno cyklu*. Ilustracja kontrolkę przycisku pokrętła znajduje się [o Up-Down — formanty](/windows/desktop/Controls/up-down-controls) w zestawie Windows SDK.

Aby utworzyć kontrolki pokrętła i okno cyklu kontrolki edycji w programie Visual Studio, przeciągnij formant edycji do okna dialogowego lub okna, a następnie przeciągnij kontrolki pokrętła. Wybierz kontrolki pokrętła i ustaw jego **automatyczne Zaprzyjaźnianie** i **Ustaw Buddy Integer** właściwości **True**. Również ustawić **wyrównanie** właściwości **Wyrównaj do prawej** najbardziej typowy. Przy użyciu tych ustawień jest ustawiony jako okno cyklu kontrolki edycji, ponieważ bezpośrednio poprzedza kontrolki edycji w kolejności tabulacji. Kontrolka edycji wyświetli liczb całkowitych i kontrolki pokrętła jest osadzony w prawej części kontrolki edycji. Opcjonalnie, należy określić prawidłowy zakres kontrolki pokrętła przy użyciu [CSpinButtonCtrl::SetRange](../mfc/reference/cspinbuttonctrl-class.md#setrange) metody. Nie obsługi zdarzeń są wymagane do komunikacji między kontrolki pokrętła i okno cyklu, ponieważ ich wymiany danych bezpośrednio. Jeśli używasz kontrolki pokrętła do niektórych innych celów, na przykład stronie przez system windows lub w oknach dialogowych, następnie Dodaj program obsługi komunikatów UDN_DELTAPOS i wykonywania akcji niestandardowej.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat

- [Style przycisku pokrętła](../mfc/spin-button-styles.md)

- [Funkcje składowe przycisku pokrętła](../mfc/spin-button-member-functions.md)

## <a name="see-also"></a>Zobacz też

[Kontrolki](../mfc/controls-mfc.md)

