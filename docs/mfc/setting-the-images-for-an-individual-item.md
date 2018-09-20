---
title: Ustawianie obrazów dla pojedynczego elementu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- extended combo boxes [MFC], images
- images [MFC], combo box items
ms.assetid: bde83db8-23a7-4e35-837a-c86447d2c0af
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9ddf2f3a57511e227a934f11262f46b528dc20aa
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46373493"
---
# <a name="setting-the-images-for-an-individual-item"></a>Ustawianie obrazów dla pojedynczego elementu

Różne rodzaje obrazy używane przez element pola kombi rozszerzone są określane przez wartości w *iImage*, *iSelectedImage*, i *iOverlay* członkowie [ COMBOBOXEXITEM](/windows/desktop/api/commctrl/ns-commctrl-tagcomboboxexitema) struktury. Każda wartość jest indeks obrazu, na liście skojarzony obraz kontrolki. Domyślnie te elementy członkowskie są ustawione na 0, powodując kontrolka do wyświetlenia nie obraz dla elementu. Jeśli chcesz używać obrazów dla określonego elementu, można zmodyfikować struktury w związku z tym podczas wstawiania elementu pola kombi lub modyfikując istniejący element pola kombi.

## <a name="setting-the-image-for-a-new-item"></a>Ustawienie obrazu dla nowego elementu

W przypadku wstawiania nowego elementu zainicjować *iImage*, *iSelectedImage*, i *iOverlay* elementy członkowskie z odpowiednimi wartościami struktury, a następnie wstawianie elementu z wywołaniem [CComboBoxEx::InsertItem](../mfc/reference/ccomboboxex-class.md#insertitem).

Poniższy przykład ilustruje wstawienie nowego elementu pola kombi rozszerzone (`cbi`) w formancie rozszerzonego pola kombi (`m_comboEx`), podając indeksów dla wszystkich trzech obrazem stany:

[!code-cpp[NVC_MFCControlLadenDialog#12](../mfc/codesnippet/cpp/setting-the-images-for-an-individual-item_1.cpp)]

## <a name="setting-the-image-for-an-existing-item"></a>Ustawienie obrazu istniejącego elementu

W przypadku modyfikowania istniejącego elementu, musisz pracować *maski* członkiem **COMBOBOXEXITEM** struktury.

#### <a name="to-modify-an-existing-item-to-use-images"></a>Aby zmodyfikować istniejący element, aby używać obrazów

1. Zadeklaruj **COMBOBOXEXITEM** struktury i ustaw *maski* element członkowski danych do wartości interesuje Cię modyfikowania.

1. Za pomocą tej struktury wywołania [CComboBoxEx::GetItem](../mfc/reference/ccomboboxex-class.md#getitem).

1. Modyfikowanie *maski*, *iImage*, i *iSelectedImage* elementy członkowskie nowo zwróconej struktury, przy użyciu odpowiednich wartości.

1. Wywołanie [CComboBoxEx::SetItem](../mfc/reference/ccomboboxex-class.md#setitem), przekazując zmodyfikowanej struktury.

W poniższym przykładzie pokazano tej procedury przez zamianę obrazów zaznaczone i niezaznaczone trzeci element pola kombi rozszerzonej:

[!code-cpp[NVC_MFCControlLadenDialog#13](../mfc/codesnippet/cpp/setting-the-images-for-an-individual-item_2.cpp)]

## <a name="see-also"></a>Zobacz też

[Korzystanie z CComboBoxEx](../mfc/using-ccomboboxex.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)

