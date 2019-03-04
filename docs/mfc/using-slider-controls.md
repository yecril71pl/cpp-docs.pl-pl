---
title: Używanie formantów suwaka
ms.date: 11/04/2016
helpviewer_keywords:
- CSliderCtrl class [MFC], using
- slider controls
- slider controls [MFC], using
ms.assetid: 2b1a8ac8-2b17-41e1-aa24-83c1fd737049
ms.openlocfilehash: b358b4e92c7d9f214291b047a080f71b48183519
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57284141"
---
# <a name="using-slider-controls"></a>Używanie formantów suwaka

Typowy kontrolki suwak jest zgodny ze wzorcem poniżej:

- Formant zostanie utworzony. Kontrolka została określona w szablonu okna dialogowego, tworzenie przebiega automatycznie podczas tworzenia okna dialogowego. (Powinien mieć [z CSliderCtrl](../mfc/reference/csliderctrl-class.md) członka klasy okien dialogowych, umożliwiająca kontrolki slider.) Alternatywnie, można użyć [Utwórz](../mfc/reference/csliderctrl-class.md#create) funkcja elementu członkowskiego, aby utworzyć formant jako okna podrzędnego każdego okna.

- Wywołaj różnych funkcji składowych zestawu, aby ustawić wartości dla formantu. Zmiany, które można wprowadzić obejmują ustawienia dla suwak w pozycji minimalną i maksymalną, rysowania znaczniki, ustawienie zaznaczony zakres i położenie suwaka. W przypadku kontrolek w oknie dialogowym jest odpowiedni moment, aby to zrobić, w oknie dialogowym [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog) funkcji.

- Jako użytkownik wchodzi w interakcję z kontrolką, wysyła komunikaty powiadomień dotyczących różnych. Wartość suwaka można wyodrębnić z kontrolki, wywołując [GetPos](../mfc/reference/csliderctrl-class.md#getpos) funkcja elementu członkowskiego.

- Po wykonaniu tych czynności za pomocą kontrolki musisz upewnij się, że jest prawidłowo niszczone. Jeśli formant suwaka znajduje się w oknie dialogowym go i `CSliderCtrl` obiekt jest niszczony automatycznie. Jeśli nie, musisz upewnij się, że obie kontrolki i `CSliderCtrl` obiektu są poprawnie niszczone.

## <a name="see-also"></a>Zobacz także

[Korzystanie z CSliderCtrl](../mfc/using-csliderctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)
