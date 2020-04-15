---
title: Korzystanie z CSpinButtonCtrl
ms.date: 11/04/2016
helpviewer_keywords:
- up-down controls [MFC], spin button control
- up-down controls
- spin button control
- CSpinButtonCtrl class [MFC], using
ms.assetid: a91db36b-e11e-42ef-8e89-51915cc486d2
ms.openlocfilehash: 6f72601d3813f36e4a99b9ab04f2e9383c58df94
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366480"
---
# <a name="using-cspinbuttonctrl"></a>Korzystanie z CSpinButtonCtrl

Formant *przycisku pokrętła* (znany również jako formant *w górę w dół)* zawiera parę strzałek, które użytkownik może kliknąć, aby dostosować wartość. Ta wartość jest znana jako *bieżąca pozycja*. Pozycja pozostaje w zasięgu przycisku pokrętła. Gdy użytkownik kliknie strzałkę w górę, pozycja przesuwa się w kierunku maksimum; a gdy użytkownik kliknie strzałkę w dół, pozycja przesuwa się w kierunku minimum.

Formant przycisku pokrętła jest reprezentowany w MFC przez [CSpinButtonCtrl](../mfc/reference/cspinbuttonctrl-class.md) klasy.

> [!NOTE]
> Domyślnie zakres przycisku spin ma maksymalną ustawioną wartość zero (0), a minimalną ustawioną na 100. Ponieważ wartość maksymalna jest mniejsza niż wartość minimalna, kliknięcie strzałki w górę zmniejsza pozycję, a kliknięcie strzałki w dół zwiększa ją. Aby dostosować te wartości, użyj [CSpinButtonCtrl::SetRange.](../mfc/reference/cspinbuttonctrl-class.md#setrange)

Zazwyczaj bieżąca pozycja jest wyświetlana w formancie towarzyszącym. Formant towarzyszący jest znany jako *okno buddy*. Aby uzyskać ilustrację sterowania przyciskiem pokrętła, zobacz [Informacje o formantach w górę i w dół](/windows/win32/Controls/up-down-controls) w panelu Windows SDK.

Aby utworzyć kontrolkę spin i okno buddy formantu edycji, w programie Visual Studio najpierw przeciągnij kontrolkę edycji do okna dialogowego lub okna, a następnie przeciągnij kontrolkę spin. Wybierz kontrolka spin i ustaw jego **właściwości Auto Buddy** i Ustaw wartość Całkowita **buddy** na **True**. Ustaw również **właściwość Wyrównanie;** **Wyrównanie do prawej** jest najbardziej typowe. W tych ustawieniach formant edycji jest ustawiany jako okno buddy, ponieważ bezpośrednio poprzedza kontrolkę edycji w kolejności kart. Formant edycji wyświetla liczby całkowite, a formant spin jest osadzony po prawej stronie formantu edycji. Opcjonalnie można ustawić prawidłowy zakres kontroli spin przy użyciu [CSpinButtonCtrl::SetRange](../mfc/reference/cspinbuttonctrl-class.md#setrange) metody. Żadne programy obsługi zdarzeń nie są wymagane do komunikowania się między formantem spin i buddy okna, ponieważ wymieniają dane bezpośrednio. Jeśli używasz kontrolki spin do innego celu, na przykład do strony za pośrednictwem sekwencji okien lub okien dialogowych, a następnie dodać program obsługi dla UDN_DELTAPOS wiadomości i wykonać akcję niestandardową tam.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz wiedzieć więcej o

- [Style przycisku pokrętła](../mfc/spin-button-styles.md)

- [Funkcje członkowskie przycisku pokrętła](../mfc/spin-button-member-functions.md)

## <a name="see-also"></a>Zobacz też

[Formanty](../mfc/controls-mfc.md)
