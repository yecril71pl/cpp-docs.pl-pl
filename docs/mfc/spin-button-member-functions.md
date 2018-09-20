---
title: Funkcje Członkowskie przycisku pokrętła | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- spin button control, methods
- CSpinButtonCtrl class [MFC], methods
ms.assetid: a08a26fd-b803-4cbe-a509-395fa357d057
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 88f00aedcf269996277c154f9dd051534a9c5e49
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46431535"
---
# <a name="spin-button-member-functions"></a>Funkcje członkowskie przycisku pokrętła

Brak dostępnych kilka elementów członkowskich dla kontrolki pokrętła ([CSpinButtonCtrl](../mfc/reference/cspinbuttonctrl-class.md)). Użyj tych funkcji, aby zmienić następujące atrybuty przycisku pokrętła.

- **Przyspieszanie** można dostosować szybkość jaką położenia zmienia się po użytkownik posiada przycisk strzałki w dół. Aby pracować z przyspieszenia, należy użyć [SetAccel](../mfc/reference/cspinbuttonctrl-class.md#setaccel) i [GetAccel](../mfc/reference/cspinbuttonctrl-class.md#getaccel) funkcji elementów członkowskich.

- **Podstawowy** można zmienić podstawowej (10 lub 16) używany do wyświetlania pozycji w podpisie okna zaprzyjaźnionego. Aby pracować z podstawowej, użyj [getbase —](../mfc/reference/cspinbuttonctrl-class.md#getbase) i [SetBase](../mfc/reference/cspinbuttonctrl-class.md#setbase) funkcji elementów członkowskich.

- **Kolega okna** można dynamicznie ustawiać okno cyklu. Aby zapytania lub zmiany, które określają to okno buddy, użyj [GetBuddy](../mfc/reference/cspinbuttonctrl-class.md#getbuddy) i [SetBuddy](../mfc/reference/cspinbuttonctrl-class.md#setbuddy) funkcji elementów członkowskich.

- **Pozycja** można wykonywać zapytania i zmiana położenia. Aby pracować bezpośrednio z pozycji, użyj [GetPos](../mfc/reference/cspinbuttonctrl-class.md#getpos) i [SetPos](../mfc/reference/cspinbuttonctrl-class.md#setpos) funkcji elementów członkowskich. Ponieważ podpis formantu partnera mogły ulec zmianie (na przykład w przypadku kolega to formant edycji) `GetPos` pobiera bieżącego podpisu i w związku z tym Dopasowuje pozycję.

- **Zakres** można zmienić położenie maksymalne i minimalne dla przycisku pokrętła. Domyślnie maksymalna jest ustawiona na 0, a minimalna jest równa 100. Ponieważ domyślna wartość maksymalna jest mniejsza niż minimalna domyślne, akcje przycisków strzałek jest counter-intuitive. Zazwyczaj spowoduje ustawienie przy użyciu zakresu [SetRange](../mfc/reference/cspinbuttonctrl-class.md#setrange) funkcja elementu członkowskiego. Do wykonywania zapytań Użyj zakresu [getrange —](../mfc/reference/cspinbuttonctrl-class.md#getrange).

## <a name="see-also"></a>Zobacz też

[Korzystanie ze CSpinButtonCtrl](../mfc/using-cspinbuttonctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)

