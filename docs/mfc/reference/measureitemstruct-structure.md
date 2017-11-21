---
title: Struktura MEASUREITEMSTRUCT | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: MEASUREITEMSTRUCT
dev_langs: C++
helpviewer_keywords: MEASUREITEMSTRUCT structure [MFC]
ms.assetid: d141ace4-47cb-46b5-a81c-ad2c5e5a8501
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: ee54b10c4eddb272653615caa7ef7ba62f707622
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="measureitemstruct-structure"></a>Struktura MEASUREITEMSTRUCT
`MEASUREITEMSTRUCT` Struktury powiadamia okno wymiarów elementu menu lub formant rysowanych przez właściciela.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef struct tagMEASUREITEMSTRUCT {  
    UINT CtlType;  
    UINT CtlID;  
    UINT itemID;  
    UINT itemWidth;  
    UINT itemHeight;  
    DWORD itemData  
} MEASUREITEMSTRUCT;  
```  
  
#### <a name="parameters"></a>Parametry  
 `CtlType`  
 Zawiera typ formantu. Wartości dla typów kontroli są następujące:  
  
- **ODT_COMBOBOX** rysowania przez właściciela pole kombi  
  
- **ODT_LISTBOX** rysowania przez właściciela pole listy  
  
- **ODT_MENU** rysowania przez właściciela menu  
  
 `CtlID`  
 Zawiera identyfikator kontrolki pola kombi, pole listy lub przycisku. Ten element członkowski nie jest używany do menu.  
  
 `itemID`  
 Zawiera identyfikator elementu menu dla menu lub identyfikator elementu pola listy zmiennej wysokości kombi lub pola listy. Ten element członkowski nie jest używany dla pola kombi wysokości pola listy lub przycisku.  
  
 *itemWidth*  
 Określa szerokość elementu menu. Właściciel elementu menu rysowania przez właściciela, należy podać ten element członkowski, przed zwróceniem z komunikatu.  
  
 *itemHeight*  
 Określa wysokość pojedynczego elementu w polu listy lub menu. Przed zwróceniem z komunikatu właściciela pole kombi rysowania przez właściciela pole listy lub elementu menu musisz wypełnić tego elementu członkowskiego. Maksymalna wysokość elementu pola listy wynosi 255.  
  
 `itemData`  
 Pola kombi lub pola listy tego elementu członkowskiego zawiera wartość, która została przekazana do pola listy przez jedną z następujących czynności:  
  
- [CComboBox::AddString](../../mfc/reference/ccombobox-class.md#addstring)  
  
- [CComboBox::InsertString](../../mfc/reference/ccombobox-class.md#insertstring)  
  
- [CListBox::AddString](../../mfc/reference/clistbox-class.md#addstring)  
  
- [CListBox::InsertString](../../mfc/reference/clistbox-class.md#insertstring)  
  
 Do menu tego elementu członkowskiego zawiera wartość, która została przekazana do menu za pomocą jednej z następujących czynności:  
  
- [CMenu::AppendMenu](../../mfc/reference/cmenu-class.md#appendmenu)  
  
- [CMenu::InsertMenu](../../mfc/reference/cmenu-class.md#insertmenu)  
  
- [CMenu::ModifyMenu](../../mfc/reference/cmenu-class.md#modifymenu)  
  
 Dzięki temu system Windows, aby poprawnie przetworzyć interakcji z formantem. Nie można wypełnić odpowiednie elementy członkowskie w `MEASUREITEMSTRUCT` struktury spowoduje, że nieprawidłowej operacji formantu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** winuser.h  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CWnd::OnMeasureItem](../../mfc/reference/cwnd-class.md#onmeasureitem)

