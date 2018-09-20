---
title: Struktura MEASUREITEMSTRUCT | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- MEASUREITEMSTRUCT
dev_langs:
- C++
helpviewer_keywords:
- MEASUREITEMSTRUCT structure [MFC]
ms.assetid: d141ace4-47cb-46b5-a81c-ad2c5e5a8501
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: db24d772e2f007b3350443ae6bc84f97cac34e76
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46397770"
---
# <a name="measureitemstruct-structure"></a>Struktura MEASUREITEMSTRUCT

`MEASUREITEMSTRUCT` Struktury informuje Windows wymiary elementu menu lub kontrolki rysowane przez właściciela.

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

*CtlType*<br/>
Zawiera typ formantu. Wartości dla typów formantów są następujące:

- Pole kombi rysowanego przez właściciela ODT_COMBOBOX

- Pole listy rysowane przez właściciela ODT_LISTBOX

- ODT_MENU rysowanym przez właściciela menu

*CtlID*<br/>
Zawiera identyfikator formantu dla pola kombi, pole listy lub przycisku. Ten element członkowski nie jest używana do menu.

*Identyfikator elementu*<br/>
Zawiera identyfikator elementu menu do menu lub identyfikator elementu pola listy, pola kombi o zmiennej wysokości lub pola listy. Ten element członkowski nie jest używana dla pola kombi wysokości lub pola listy lub dla przycisku.

*itemWidth*<br/>
Określa szerokość elementu menu. Właściciel elementu menu rysowania przez właściciela należy podać ten element członkowski, przed zwróceniem z komunikatu.

*itemHeight*<br/>
Określa wysokość pojedynczy element w polu listy lub menu. Przed zwróceniem z komunikatu właściciela pole kombi rysowanego przez właściciela pola listy i element menu musisz wypełnić tego elementu członkowskiego. Maksymalna wysokość elementu pola listy wynosi 255.

*itemData*<br/>
Pole kombi lub pola listy ten element członkowski zawiera wartość, która została przekazana do pola listy za pomocą jednej z następujących czynności:

- [CComboBox::AddString](../../mfc/reference/ccombobox-class.md#addstring)

- [CComboBox::InsertString](../../mfc/reference/ccombobox-class.md#insertstring)

- [CListBox::AddString](../../mfc/reference/clistbox-class.md#addstring)

- [CListBox::InsertString](../../mfc/reference/clistbox-class.md#insertstring)

Do menu tego elementu członkowskiego zawiera wartość, która została przekazana do menu za pomocą jednej z następujących czynności:

- [CMenu::AppendMenu](../../mfc/reference/cmenu-class.md#appendmenu)

- [CMenu::InsertMenu](../../mfc/reference/cmenu-class.md#insertmenu)

- [CMenu::ModifyMenu](../../mfc/reference/cmenu-class.md#modifymenu)

Dzięki temu Windows poprawnie przetworzyć interakcji z użytkownikiem za pomocą kontrolki. Błąd występujący w odpowiednich elementów członkowskich `MEASUREITEMSTRUCT` struktury spowoduje, że nieprawidłowej operacji formantu.

## <a name="requirements"></a>Wymagania

**Nagłówek:** winuser.h

## <a name="see-also"></a>Zobacz też

[Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CWnd::OnMeasureItem](../../mfc/reference/cwnd-class.md#onmeasureitem)

