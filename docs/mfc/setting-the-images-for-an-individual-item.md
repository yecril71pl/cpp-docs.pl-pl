---
title: Ustawianie obrazów dla pojedynczego elementu
ms.date: 11/04/2016
helpviewer_keywords:
- extended combo boxes [MFC], images
- images [MFC], combo box items
ms.assetid: bde83db8-23a7-4e35-837a-c86447d2c0af
ms.openlocfilehash: 177c06acfe665a43921b19407d9d357d4545e748
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69511275"
---
# <a name="setting-the-images-for-an-individual-item"></a>Ustawianie obrazów dla pojedynczego elementu

Różne typy obrazów używane przez rozszerzony element pola kombi są określane przez wartości w *IImage*, *iSelectedImage*i *IOverlay* elementów członkowskich struktury [COMBOBOXEXITEM](/windows/win32/api/commctrl/ns-commctrl-comboboxexitemw) . Każda wartość jest indeksem obrazu na liście skojarzonych obrazów kontrolki. Domyślnie te elementy członkowskie są ustawione na 0, co sprawia, że kontrolka nie wyświetla obrazu dla elementu. Jeśli chcesz użyć obrazów dla określonego elementu, możesz odpowiednio zmodyfikować strukturę, podczas wstawiania elementu pola kombi lub modyfikując istniejący element pola kombi.

## <a name="setting-the-image-for-a-new-item"></a>Ustawianie obrazu dla nowego elementu

Jeśli wstawiasz nowy element, zainicjuj elementy członkowskie struktury *IImage*, *iSelectedImage*i *IOverlay* przy użyciu odpowiednich wartości, a następnie Wstaw element z wywołaniem do [Korzystanie CComboBoxEx:: InsertItem](../mfc/reference/ccomboboxex-class.md#insertitem).

Poniższy przykład wstawia nowy rozszerzony element pola kombi (`cbi`) do kontrolki rozszerzonego pola kombi (`m_comboEx`), dostarczając indeksy dla wszystkich trzech stanów obrazu:

[!code-cpp[NVC_MFCControlLadenDialog#12](../mfc/codesnippet/cpp/setting-the-images-for-an-individual-item_1.cpp)]

## <a name="setting-the-image-for-an-existing-item"></a>Ustawianie obrazu dla istniejącego elementu

W przypadku modyfikowania istniejącego elementu należy współpracować z elementem członkowskim *maski* struktury **COMBOBOXEXITEM** .

#### <a name="to-modify-an-existing-item-to-use-images"></a>Aby zmodyfikować istniejący element, aby użyć obrazów

1. Zadeklaruj strukturę **COMBOBOXEXITEM** i Ustaw element członkowski danych *maski* na wartości, które chcesz zmodyfikować.

1. Przy użyciu tej struktury należy wywołać metodę [Korzystanie CComboBoxEx:: GetItem](../mfc/reference/ccomboboxex-class.md#getitem).

1. Zmodyfikuj elementy członkowskie *Mask*, *IImage*i *iSelectedImage* w nowo zwracanej strukturze przy użyciu odpowiednich wartości.

1. Wykonaj wywołanie [Korzystanie CComboBoxEx:: SetItem](../mfc/reference/ccomboboxex-class.md#setitem), przekazując do zmodyfikowanej struktury.

Poniższy przykład ilustruje tę procedurę, zamieniając wybrane i niewybrane obrazy trzeciego rozszerzonego pola kombi:

[!code-cpp[NVC_MFCControlLadenDialog#13](../mfc/codesnippet/cpp/setting-the-images-for-an-individual-item_2.cpp)]

## <a name="see-also"></a>Zobacz także

[Korzystanie z CComboBoxEx](../mfc/using-ccomboboxex.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)
