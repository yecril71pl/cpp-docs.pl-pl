---
title: Struktura DRAWITEMSTRUCT | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: DRAWITEMSTRUCT
dev_langs: C++
helpviewer_keywords: DRAWITEMSTRUCT structure [MFC]
ms.assetid: ba9ef1d4-aebb-45e9-b956-4b81a02e50f7
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 438d698b486b455d7898a836d510aa5ec1c6e454
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="drawitemstruct-structure"></a>Struktura DRAWITEMSTRUCT
`DRAWITEMSTRUCT` Struktury informuje okno właściciela musi mieć do określania, jak namalować elementu menu lub formant rysowanych przez właściciela.  
  
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
 `CtlType`  
 Typ formantu. Wartości dla typów kontroli są następujące:  
  
- **ODT_BUTTON** przyciskiem rysowanym przez właściciela  
  
- **ODT_COMBOBOX** pola kombi rysowanych przez właściciela  
  
- **ODT_LISTBOX** pole listy rysowane przez właściciela  
  
- **ODT_MENU** rysowanych przez właściciela menu  
  
- **ODT_LISTVIEW** formantu widoku listy  
  
- **ODT_STATIC** rysowanych przez właściciela statyczną kontrolkę  
  
- **ODT_TAB** karcie formantu  
  
 `CtlID`  
 Identyfikator formantu dla pola kombi, pole listy lub przycisku. Ten element członkowski nie jest używany do menu.  
  
 `itemID`  
 Identyfikator elementu menu dla menu lub indeks elementu w polu listy lub pola kombi. Lista jest pusta lub polu kombi, ten element członkowski jest wartością ujemną, dzięki czemu aplikacji do rysowania tylko prostokąt fokusu we współrzędnych określonych przez **rcItem** Członkowskie nawet wtedy, gdy nie ma żadnych towarów w formancie. W związku z tym można pokazać użytkownika czy pole listy lub pole kombi ma fokus wprowadzania. Ustawienie usługi bits w **itemAction** elementu członkowskiego Określa, czy ma być rysowany tak, jakby pole listy lub pole kombi ma wejściowych fokus prostokąta.  
  
 `itemAction`  
 Definiuje rysowania czynności. Może to mieć co najmniej jeden z następujących bitów:  
  
- **ODA_DRAWENTIRE** ten bit jest ustawiona, gdy potrzebne jest narysowanie całego formantu.  
  
- **ODA_FOCUS** ten bit jest ustawiony, gdy formant uzyska lub utraci fokus wprowadzania. **ItemState** Członkowskie powinny być sprawdzane w celu określenia, czy formant ma fokus.  
  
- **ODA_SELECT** ten bit jest ustawiony, gdy zostanie zmieniony stan zaznaczenia. **ItemState** elementu członkowskiego powinien być sprawdzany w celu określenia nowy stan zaznaczenia.  
  
 *itemState*  
 Określa stanu wizualnego elementu po wystąpieniu rysowania bieżącej akcji. Oznacza to, czy element menu jest być nieaktywne, flagi stanu **ODS_GRAYED** zostanie ustawiona. Flagi stanu są następujące:  
  
- **ODS_CHECKED** ten bit jest ustawiona, jeśli element menu ma być sprawdzony. Ten bit jest używana tylko w menu.  
  
- **ODS_DISABLED** ten bit jest ustawiona, jeśli element ma być rysowany jako wyłączone.  
  
- **ODS_FOCUS** ten bit jest ustawiona, jeśli element ma wejściowych fokus.  
  
- **ODS_GRAYED** ten bit jest ustawiona, jeśli element znajduje się na wygaszone. Ten bit jest używana tylko w menu.  
  
- **ODS_SELECTED** ten bit jest ustawiony, jeśli stan elementu jest zaznaczone.  
  
- **ODS_COMBOBOXEDIT** rysunku odbywa się w polu Wybór (kontrolki edycji) ownerdrawn pola kombi.  
  
- **ODS_DEFAULT** element jest elementem domyślnym.  
  
 `hwndItem`  
 Określa uchwytu okna kontrolki pola kombi, pola listy i przycisków. Określa dojście menu (`HMENU`) zawierający element menu.  
  
 `hDC`  
 Identyfikuje kontekst urządzenia. Ten kontekst urządzenia należy użyć podczas wykonywania operacji rysowania w formancie.  
  
 *rcItem*  
 Prostokąt w kontekście urządzenia określonego przez `hDC` elementu członkowskiego, który definiuje granice formantu do narysowania. System Windows automatycznie klipy coś właściciela rysuje kontekstu urządzenia dla pola kombi, pola listy i przyciski, ale go nie obcina elementów menu. Podczas rysowania elementów menu, właściciel musi nie Rysuj poza obszarem prostokąta zdefiniowane przez **rcItem** elementu członkowskiego.  
  
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
  
## <a name="remarks"></a>Uwagi  
 Okno właściciela elementu menu lub formant rysowanych przez właściciela otrzymuje wskaźnik tej struktury jako `lParam` parametr `WM_DRAWITEM` wiadomości.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** winuser.h  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CWnd::OnDrawItem](../../mfc/reference/cwnd-class.md#ondrawitem)

