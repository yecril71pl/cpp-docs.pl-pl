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
ms.openlocfilehash: a2a12672f0e70248e135bdd177b76589b6197c75
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69513464"
---
# <a name="using-cspinbuttonctrl"></a>Korzystanie z CSpinButtonCtrl

Kontrolka *przycisku pokrętła* (nazywana również kontrolką *w górę* ) zawiera parę strzałek, które użytkownik może kliknąć, aby dostosować wartość. Ta wartość jest określana jako *Bieżąca pozycja*. Pozycja pozostaje poza zakresem przycisku pokrętła. Gdy użytkownik kliknie strzałkę w górę, pozycja przesuwa się w kierunku maksimum; gdy użytkownik kliknie strzałkę w dół, pozycja przesuwa się w kierunku minimum.

Kontrolka przycisku pokrętła jest reprezentowana w MFC przez klasę [Korzystanie CSpinButtonCtrl](../mfc/reference/cspinbuttonctrl-class.md) .

> [!NOTE]
>  Domyślnie zakres dla przycisku pokrętła ma ustawioną wartość równą zero (0) i minimalną ustawioną na 100. Ponieważ wartość maksymalna jest mniejsza niż wartość minimalna, kliknięcie strzałki w górę zmniejsza pozycję i klika strzałkę w dół. Użyj [Korzystanie CSpinButtonCtrl:: SetRange](../mfc/reference/cspinbuttonctrl-class.md#setrange) , aby dostosować te wartości.

Zazwyczaj bieżąca pozycja jest wyświetlana w formancie pomocnika. Formant pomocnika jest znany jako *okno partnera*. Ilustracja kontrolki przycisku pokrętła znajduje się w temacie [Informacje o kontrolkach w dół](/windows/win32/Controls/up-down-controls) w Windows SDK.

Aby utworzyć kontrolkę pokrętła i okno dialogowe Edytowanie formantu kolega, w programie Visual Studio, najpierw przeciągnij kontrolkę Edycja do okna dialogowego lub okno, a następnie przeciągnij kontrolkę pokrętła. Wybierz kontrolkę pokrętła i ustaw jej właściwości autozaprzyjaźnione i **Ustaw opcję kolega Integer** na **wartość true**. Ustaw również właściwość **wyrównania** . **Wyrównanie do prawej** jest najbardziej typowe. Przy użyciu tych ustawień kontrolka edycji jest ustawiana jako okno kolega, ponieważ bezpośrednio poprzedza kontrolkę Edycja w kolejności tabulacji. Kontrolka edycji wyświetla liczby całkowite, a kontrolka pokrętła jest osadzona po prawej stronie kontrolki edycji. Opcjonalnie można ustawić prawidłowy zakres kontrolki pokrętła przy użyciu metody [Korzystanie CSpinButtonCtrl:: SetRange](../mfc/reference/cspinbuttonctrl-class.md#setrange) . Do komunikacji między kontrolką i oknem kolega nie są wymagane programy obsługi zdarzeń, ponieważ wymieniają one bezpośrednio dane. Jeśli używasz kontrolki pokrętła do innych celów, na przykład do strony za pomocą sekwencji okien dialogowych lub okna dialogowego, Dodaj procedurę obsługi dla komunikatu UDN_DELTAPOS i wykonaj w niej akcję niestandardową.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o

- [Style przycisku pokrętła](../mfc/spin-button-styles.md)

- [Funkcje składowe przycisku pokrętła](../mfc/spin-button-member-functions.md)

## <a name="see-also"></a>Zobacz także

[Kontrolki](../mfc/controls-mfc.md)
