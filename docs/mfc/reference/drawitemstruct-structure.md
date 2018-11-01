---
title: Struktura DRAWITEMSTRUCT
ms.date: 11/04/2016
f1_keywords:
- DRAWITEMSTRUCT
helpviewer_keywords:
- DRAWITEMSTRUCT structure [MFC]
ms.assetid: ba9ef1d4-aebb-45e9-b956-4b81a02e50f7
ms.openlocfilehash: 9c5bfc12bd371761682102dad6d7bcb75ef44151
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50624435"
---
# <a name="drawitemstruct-structure"></a>Struktura DRAWITEMSTRUCT

`DRAWITEMSTRUCT` Struktura zawiera informacje, które musi mieć okno właściciela, aby określić, jak namalować elementu menu lub kontrolki rysowane przez właściciela.

## <a name="syntax"></a>Składnia

```
typedef struct tagDRAWITEMSTRUCT {
    UINT CtlType;
    UINT CtlID;
    UINT itemID;
    UINT itemAction;
    UINT itemState;
    HWND hwndItem;
    HDC hDC;
    RECT rcItem;
    DWORD itemData;
} DRAWITEMSTRUCT;
```

#### <a name="parameters"></a>Parametry

*CtlType*<br/>
Typ formantu. Wartości dla typów formantów są następujące:

- ODT_BUTTON przyciskiem rysowanym przez właściciela

- Pole kombi rysowanych przez właściciela ODT_COMBOBOX

- Pole listy rysowane przez właściciela ODT_LISTBOX

- ODT_MENU rysowanych przez właściciela menu

- Kontrolka widoku listy ODT_LISTVIEW

- ODT_STATIC rysowanych przez właściciela statyczną kontrolkę

- Kontrolka karty ODT_TAB

*CtlID*<br/>
Identyfikator formantu dla pola kombi, pole listy lub przycisku. Ten element członkowski nie jest używana do menu.

*Identyfikator elementu*<br/>
Identyfikator elementu menu menu lub indeks elementu w polu listy lub pola kombi. Jeśli lista jest pusta lub polu kombi, ten element członkowski jest wartością ujemną umożliwia aplikacji rysowania tylko prostokąt fokusu we współrzędnych określonych przez `rcItem` nawet wtedy, gdy brak elementów w kontrolce elementu członkowskiego. Użytkownik ten sposób mogą być wyświetlane, czy pole listy lub pola kombi ma fokusa wejścia. Ustawienia usługi bits w `itemAction` elementu członkowskiego Określa, czy ma być rysowany tak, jakby pola listy lub pola kombi ma fokus wejścia prostokąta.

*itemAction*<br/>
Definiuje rysowania czynności. Może to mieć co najmniej jeden z następujących bitów:

- ODA_DRAWENTIRE ten bit jest ustawiona, gdy kontrolka całego wymaga do narysowania.

- ODA_FOCUS ten bit jest ustawiona, gdy kontrolka zyskuje lub traci fokus wprowadzania. `itemState` Elementu członkowskiego powinny być sprawdzane w celu ustalenia, czy kontrolka ma fokus.

- ODA_SELECT ten bit jest ustawiony, gdy zmieniono tylko stan zaznaczenia. `itemState` Członkowskie powinny być sprawdzane, aby określić nowy stan zaznaczenia.

*itemState*<br/>
Określa stan wizualny elementu po wystąpieniu bieżącej akcji rysowania. Oznacza to jeśli element menu jest wyszarzony, flagi stanu ODS_GRAYED zostaną ustawione. Flagi stanu są następujące:

- ODS_CHECKED ten bit jest ustawiona, jeśli element menu ma zostać sprawdzony. Ten bit jest używany tylko w menu.

- ODS_DISABLED ten bit jest ustawiona, jeśli element ma być rysowany jako wyłączone.

- ODS_FOCUS ten bit jest ustawiona, jeśli element ma fokus wejścia.

- ODS_GRAYED ten bit jest ustawiona, jeśli element jest wyszarzony. Ten bit jest używany tylko w menu.

- ODS_SELECTED ten bit jest ustawiona, jeśli wybrano opcję stan elementu.

- ODS_COMBOBOXEDIT rysunek odbywa się w polu wyboru (kontrolki edycji) ownerdrawn pola kombi.

- ODS_DEFAULT element to element domyślny.

*hwndItem*<br/>
Określa uchwyt okna formantu dla pola kombi, pola listy i przyciski. Określa uchwyt menu (HMENU), który zawiera element menu.

*elementu hDC*<br/>
Identyfikuje kontekst urządzenia. Podczas wykonywania operacji rysowania w kontrolce, należy użyć tego kontekstu urządzenia.

*rcItem*<br/>
Prostokąt w kontekście urządzenia określone przez *elementu hDC* elementu członkowskiego, który definiuje granice kontrolki do rysowania. Windows automatycznie przycina coś, czego właściciela rysuje w kontekście urządzenia dla pola kombi, pola listy i przyciski, ale go nie obcina elementów menu. Podczas rysowania elementów menu, właściciel nie należy narysować poza obszarem prostokąta zdefiniowanego przez `rcItem` elementu członkowskiego.

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

## <a name="remarks"></a>Uwagi

Okno właściciela elementu menu lub kontrolki rysowane przez właściciela otrzymuje wskaźnik do tej struktury jako *lParam* parametru WM_DRAWITEM wiadomości.

## <a name="requirements"></a>Wymagania

**Nagłówek:** winuser.h

## <a name="see-also"></a>Zobacz też

[Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CWnd::OnDrawItem](../../mfc/reference/cwnd-class.md#ondrawitem)

