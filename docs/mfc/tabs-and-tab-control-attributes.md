---
title: Karty i atrybuty formantu karty
ms.date: 11/04/2016
helpviewer_keywords:
- attributes [MFC], reference topics
- tab controls [MFC], attributes
- tabs [MFC]
- tabs [MFC], attributes
- CTabCtrl class [MFC], tab control attributes
ms.assetid: ecf190cb-f323-4751-bfdb-766dbe6bb553
ms.openlocfilehash: 982ec40e330e2a7dda5c125d83e54751cd14416d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69511244"
---
# <a name="tabs-and-tab-control-attributes"></a>Karty i atrybuty formantu karty

Masz znacznie kontrolę nad wyglądem i zachowaniem kart tworzących kontrolkę karta ([CTabCtrl](../mfc/reference/ctabctrl-class.md)). Każda karta może mieć etykietę, ikonę, stan elementu i skojarzoną z nią wartość 32-bitową. Dla każdej karty można wyświetlić ikonę, etykietę lub oba te elementy.

Ponadto każdy element karty może mieć trzy możliwe stany: naciśnięto, niekliknięty lub wyróżniony. Ten stan można ustawić tylko przez zmodyfikowanie istniejącego elementu karty. Aby zmodyfikować istniejący element karty, Pobierz go z wywołaniem do [GetItem](../mfc/reference/ctabctrl-class.md#getitem), `TCITEM` zmodyfikuj strukturę (głównie elementy członkowskie danych *dwState* i *dwStateMask* ), a następnie Zwróć zmodyfikowaną `TCITEM` strukturę z wywołaniem do [SetItem](../mfc/reference/ctabctrl-class.md#setitem). Jeśli musisz wyczyścić Stany elementu wszystkich elementów karty w `CTabCtrl` obiekcie, wykonaj wywołanie do [DeselectAll](../mfc/reference/ctabctrl-class.md#deselectall). Ta funkcja resetuje stan wszystkich elementów karty lub wszystkich elementów oprócz aktualnie wybranego.

Poniższy kod czyści stan wszystkich elementów karty, a następnie modyfikuje stan trzeciego elementu:

[!code-cpp[NVC_MFCControlLadenDialog#32](../mfc/codesnippet/cpp/tabs-and-tab-control-attributes_1.cpp)]

Aby uzyskać więcej informacji na temat atrybutów karty, zobacz [atrybuty kart i tabulatorów](/windows/win32/Controls/tab-controls) w Windows SDK. Aby uzyskać więcej informacji na temat dodawania kart do kontrolki karta, zobacz [Dodawanie kart do kontrolki karta](../mfc/adding-tabs-to-a-tab-control.md) w dalszej części tego tematu.

## <a name="see-also"></a>Zobacz także

[Korzystanie z CTabCtrl](../mfc/using-ctabctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)
