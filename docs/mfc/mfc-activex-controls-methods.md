---
title: 'Formanty MFC ActiveX: metody'
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], methods
ms.assetid: e20271de-6ffa-4ba0-848b-bafe6c9e510c
ms.openlocfilehash: 9f9ec06852ed0376583363df7649331a0be02105
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621235"
---
# <a name="mfc-activex-controls-methods"></a>Formanty MFC ActiveX: metody

Kontrolka ActiveX wyzwala zdarzenia w celu komunikacji między sobą i jego kontenerem sterowania. Kontener może również komunikować się z kontrolką przy użyciu metod i właściwości. Metody są również nazywane funkcjami.

Metody i właściwości zapewniają wyeksportowany interfejs do użytku przez inne aplikacje, takie jak klienci automatyzacji i kontenery kontrolek ActiveX. Aby uzyskać więcej informacji na temat właściwości kontrolki ActiveX, zobacz artykuł [kontrolki ActiveX MFC: właściwości](mfc-activex-controls-properties.md).

Metody są podobne do użycia i celu do funkcji składowych klasy języka C++. Istnieją dwa typy metod, które można zaimplementować dla kontrolki: giełdowe i niestandardowe. Podobnie jak w przypadku wydarzeń giełdowych, metody podstawowe to metody, dla których [COleControl](reference/colecontrol-class.md) zapewnia implementację. Aby uzyskać więcej informacji na temat metod podstawowych, zobacz artykuł [kontrolki ActiveX MFC: dodawanie metod podstawowych](mfc-activex-controls-adding-stock-methods.md). Metody niestandardowe zdefiniowane przez dewelopera umożliwiają dodatkowe dostosowanie formantu. Aby uzyskać więcej informacji, zobacz artykuł [kontrolki ActiveX MFC: dodawanie metod niestandardowych](mfc-activex-controls-adding-custom-methods.md).

Biblioteka MFC (MFC) implementuje mechanizm, który umożliwia formantowi obsługę zasobów i metod niestandardowych. Pierwsza część to Klasa `COleControl` . Pochodne `CWnd` `COleControl` funkcje składowe obsługują metody podstawowe, które są wspólne dla wszystkich kontrolek ActiveX. Drugą częścią tego mechanizmu jest mapa wysyłania. Mapa wysyłania jest podobna do mapy komunikatów; Jednak zamiast mapowania funkcji do identyfikatora komunikatu systemu Windows Mapa wysyłania mapuje wirtualne funkcje członkowskie na identyfikatory IDispatch.

Aby formant obsługiwał różne metody prawidłowo, jego Klasa musi deklarować mapę wysyłania. Jest to realizowane przez następujący wiersz kodu znajdujący się w nagłówku klasy kontrolki (. H):

[!code-cpp[NVC_MFC_AxUI#13](codesnippet/cpp/mfc-activex-controls-methods_1.h)]

Głównym celem mapy wysyłania jest ustanowienie relacji między nazwami metod, które są używane przez zewnętrzny obiekt wywołujący (na przykład kontener) i funkcje członkowskie klasy kontrolki implementującej metody. Po zadeklarowaniu mapy wysyłania należy ją zdefiniować w implementacji kontrolki (. CPP). Następujące wiersze kodu definiują mapę wysyłania:

[!code-cpp[NVC_MFC_AxUI#14](codesnippet/cpp/mfc-activex-controls-methods_2.cpp)]
[!code-cpp[NVC_MFC_AxUI#15](codesnippet/cpp/mfc-activex-controls-methods_3.cpp)]

Jeśli do utworzenia projektu użyto [Kreatora kontrolek ActiveX MFC](reference/mfc-activex-control-wizard.md) , te wiersze zostały dodane automatycznie. Jeśli Kreator kontrolek ActiveX MFC nie był używany, należy dodać te wiersze ręcznie.

W poniższych artykułach szczegółowo omówiono metody:

- [Kontrolki ActiveX MFC: dodawanie metod standardowych](mfc-activex-controls-adding-stock-methods.md)

- [Kontrolki ActiveX MFC: dodawanie metod niestandardowych](mfc-activex-controls-adding-custom-methods.md)

- [Kontrolki ActiveX MFC: zwracanie kodów błędów z metody](mfc-activex-controls-returning-error-codes-from-a-method.md)

## <a name="see-also"></a>Zobacz też

[Kontrolki ActiveX MFC](mfc-activex-controls.md)
