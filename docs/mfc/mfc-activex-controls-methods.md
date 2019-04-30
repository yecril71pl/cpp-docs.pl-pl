---
title: 'Kontrolki ActiveX MFC: Metody'
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], methods
ms.assetid: e20271de-6ffa-4ba0-848b-bafe6c9e510c
ms.openlocfilehash: 71c4cdd5ea07b3468b7878a221129a0de5eb4974
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62386372"
---
# <a name="mfc-activex-controls-methods"></a>Kontrolki ActiveX MFC: Metody

Kontrolki ActiveX uruchamia zdarzeń do komunikowania się między sobą i jego kontener formantu. Kontener również mogą komunikować się za pomocą kontrolki za pomocą metod i właściwości. Metody są również nazywane funkcji.

Metody i właściwości, należy podać wyeksportowanego interfejsu do użytku przez inne aplikacje, takie jak klienci automatyzacji i kontenery kontrolek ActiveX. Aby uzyskać więcej informacji na temat właściwości formantu ActiveX, zobacz artykuł [kontrolki ActiveX MFC: Właściwości](../mfc/mfc-activex-controls-properties.md).

Metody są podobne w użycie i przeznaczenie funkcji składowych klasy języka C++. Istnieją dwa typy metod kontroli nad można zaimplementować: standardowych i niestandardowych. Podobne do magazynu zdarzeń, akcji metody są tych metod, dla którego [COleControl](../mfc/reference/colecontrol-class.md) dostarcza implementację. Aby uzyskać więcej informacji na temat metody akcji, zobacz artykuł [kontrolki ActiveX MFC: Dodawanie metod standardowych](../mfc/mfc-activex-controls-adding-stock-methods.md). Niestandardowych metod, zdefiniowanych przez dewelopera, Zezwalaj na dodatkowe Dostosowywanie formantu. Aby uzyskać więcej informacji, zobacz artykuł [kontrolki ActiveX MFC: Dodawanie metod niestandardowych](../mfc/mfc-activex-controls-adding-custom-methods.md).

Biblioteka Microsoft Foundation Class (MFC) implementuje mechanizm umożliwiający formantu do obsługi zapasów i niestandardowych metod. Pierwsza część jest klasą `COleControl`. Pochodną `CWnd`, `COleControl` funkcji elementów członkowskich obsługuje podstawowe metody, które są wspólne dla wszystkich formantów ActiveX. Druga część ten mechanizm jest mapa wysyłania. Mapa wysyłania jest podobny do mapy komunikatów; Jednak zamiast mapowania funkcji do Identyfikatora wiadomości Windows, mapa wysyłania mapuje funkcji wirtualnych elementów członkowskich IDispatch identyfikatorów.

Kontrolki do obsługi różnych metod prawidłowo swojej klasy należy zadeklarować Mapa wysyłania. Jest to osiągane przez następujący wiersz kodu znajdujące się w nagłówku klasy formantu (. H) plik:

[!code-cpp[NVC_MFC_AxUI#13](../mfc/codesnippet/cpp/mfc-activex-controls-methods_1.h)]

Głównym celem Mapa wysyłania jest ustanowienie relacji między nazwami metody używane przez zewnętrzne obiekt wywołujący (np. kontenerze) i funkcje elementów członkowskich klasy kontrolki, które implementują metody. Po zadeklarowaniu mapy wysyłania musi być zdefiniowany w implementacji formantu (. Plik CPP). Następujące wiersze kodu, zdefiniuj Mapa wysyłania:

[!code-cpp[NVC_MFC_AxUI#14](../mfc/codesnippet/cpp/mfc-activex-controls-methods_2.cpp)]
[!code-cpp[NVC_MFC_AxUI#15](../mfc/codesnippet/cpp/mfc-activex-controls-methods_3.cpp)]

Jeśli użyto [Kreator kontrolek ActiveX MFC](../mfc/reference/mfc-activex-control-wizard.md) do tworzenia projektu, te wiersze zostały dodane automatycznie. Jeśli Kreator kontrolek ActiveX MFC nie było używane, należy ręcznie dodać następujące wiersze.

W następujących artykułach omówiono metody szczegółowo:

- [Kontrolki ActiveX MFC: dodawanie metod standardowych](../mfc/mfc-activex-controls-adding-stock-methods.md)

- [Kontrolki ActiveX MFC: dodawanie metod niestandardowych](../mfc/mfc-activex-controls-adding-custom-methods.md)

- [Kontrolki ActiveX MFC: zwracanie kodów błędów z metody](../mfc/mfc-activex-controls-returning-error-codes-from-a-method.md)

## <a name="see-also"></a>Zobacz także

[Kontrolki ActiveX MFC](../mfc/mfc-activex-controls.md)
