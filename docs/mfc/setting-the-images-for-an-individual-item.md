---
title: "Ustawianie obrazów dla pojedynczego elementu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- extended combo boxes [MFC], images
- images [MFC], combo box items
ms.assetid: bde83db8-23a7-4e35-837a-c86447d2c0af
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4d9cb74c2290292f44b8c6c9b8797890e759f315
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="setting-the-images-for-an-individual-item"></a>Ustawianie obrazów dla pojedynczego elementu
Różne typy obrazów używany przez element pola kombi rozszerzone są określane przez wartości `iImage`, **iSelectedImage**, i **iOverlay** członkami [COMBOBOXEXITEM ](http://msdn.microsoft.com/library/windows/desktop/bb775746) struktury. Każda wartość jest indeks obrazu na liście skojarzony obraz formantu. Domyślnie te elementy członkowskie są ustawione na 0, powodując kontrolka do wyświetlenia nie obraz dla elementu. Jeśli chcesz używać obrazów dla określonego elementu, można zmodyfikować struktury w związku z tym podczas wstawiania elementu pola kombi lub przez zmodyfikowanie istniejącego elementu pola kombi.  
  
## <a name="setting-the-image-for-a-new-item"></a>Ustawienia dla nowego elementu obrazu  
 W przypadku wstawiania nowego elementu zainicjować `iImage`, **iSelectedImage**, i **iOverlay** struktury elementów członkowskich o odpowiednie wartości, a następnie Wstaw element z wywołania [ CComboBoxEx::InsertItem](../mfc/reference/ccomboboxex-class.md#insertitem).  
  
 Poniższy przykład Wstawia nowy element pola kombi rozszerzonej (`cbi`) w formancie rozszerzonego pola kombi (`m_comboEx`), podając indeksów dla obrazów wszystkich trzech stanów:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#12](../mfc/codesnippet/cpp/setting-the-images-for-an-individual-item_1.cpp)]  
  
## <a name="setting-the-image-for-an-existing-item"></a>Ustawienie obraz istniejącego elementu  
 W przypadku modyfikowania istniejącego elementu potrzebne do pracy z **maski** członkiem **COMBOBOXEXITEM** struktury.  
  
#### <a name="to-modify-an-existing-item-to-use-images"></a>Aby zmodyfikować istniejący element do użycia obrazy  
  
1.  Deklarowanie **COMBOBOXEXITEM** struktury i ustaw **maski** element członkowski danych wartości interesuje Cię przy modyfikacji.  
  
2.  Przy użyciu tej struktury wywoływania [CComboBoxEx::GetItem](../mfc/reference/ccomboboxex-class.md#getitem).  
  
3.  Modyfikowanie **maski**, `iImage`, i **iSelectedImage** elementy członkowskie struktury nowo zwrócony przy użyciu odpowiednich wartości.  
  
4.  Wywoływania [CComboBoxEx::SetItem](../mfc/reference/ccomboboxex-class.md#setitem), przekazując modyfikacji struktury.  
  
 W poniższym przykładzie pokazano tej procedury przez zamianę obrazów zaznaczone i niezaznaczone trzeciego elementu pola kombi rozszerzonej:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#13](../mfc/codesnippet/cpp/setting-the-images-for-an-individual-item_2.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CComboBoxEx](../mfc/using-ccomboboxex.md)   
 [Kontrolki](../mfc/controls-mfc.md)

