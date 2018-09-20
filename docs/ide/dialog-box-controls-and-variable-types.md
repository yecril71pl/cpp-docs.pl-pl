---
title: Formanty okna dialogowego i typy zmiennych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- dialog box controls, member variables
- dialog box controls, variable types
- variables, dialog box control member variables
ms.assetid: f9cd9cea-45a6-4349-8358-e5efbcdcff76
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6914ab8b5838ee6bc5bb7a74004ed986efe2fcda
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46373990"
---
# <a name="dialog-box-controls-and-variable-types"></a>Formanty okna dialogowego i typy zmiennych

Możesz użyć [Kreator dodawania zmiennej składowej](../ide/add-member-variable-wizard.md) można dodać zmiennej składowej do kontrolki pola dialogowe utworzone za pomocą MFC. Typ kontrolki, dla którego należy dodać zmiennej składowej Określa opcje, które są wyświetlane w oknie dialogowym.

W poniższej tabeli opisano wszystkie typy okna dialogowego pole formantu, są obsługiwane w MFC i [Edytor okien dialogowych](../windows/dialog-editor.md)oraz dostępne typy i wartości.

|Formant|Typ formantu|Typ zmiennej sterującej|Typ zmiennej wartości|Minimalnej/maksymalnej wartości (tylko w przypadku typu wartości)|
|-------------|------------------|---------------------------|-------------------------|-----------------------------------------|
|Kontrolki animacji|SysAnimate32|[CAnimateCtrl](../mfc/reference/canimatectrl-class.md)|None; tylko kontroli|Brak|
|Przycisk|PRZYCISK|[CButton](../mfc/reference/cbutton-class.md)|None; tylko kontroli|Brak|
|Pole wyboru|SPRAWDŹ|[CButton](../mfc/reference/cbutton-class.md)|**BOOL**|Minimalna wartość/maksymalna wartość|
|Pole kombi|POLE KOMBI COMBOBOX|[CComboBox](../mfc/reference/ccombobox-class.md)|[CString](../atl-mfc-shared/reference/cstringt-class.md)|Maksymalna liczba znaków|
|Kontrolka selektora czasu daty|SysDateTimePick32|[CDateTimeCtrl](../mfc/reference/cdatetimectrl-class.md)|[Ctime —](../atl-mfc-shared/reference/ctime-class.md)|Minimalna wartość/maksymalna wartość|
|Pole edycji|EDYTUJ|[CEdit](../mfc/reference/cedit-class.md)|`CString`, int, UINT, long, DWORD, float, double, BYTE, short, BOOL, `COleDateTime`, lub **COleCurrency**|Minimalna wartość/maksymalna wartość; Niektóre znaki max pomocy technicznej|
|Kontrola skrótu|msctls_hotkey32|[CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)|None; tylko kontroli|Brak|
|Pole listy|POLE LISTY|[CListBox](../mfc/reference/clistbox-class.md)|`CString`|Maksymalna liczba znaków|
|Kontrolka listy|SysListView32|[CListCtrl](../mfc/reference/clistctrl-class.md)|None; tylko kontroli|Brak|
|Kontrolowanie kalendarza miesięcznego|SysMonthCal32|[CMonthCalCtrl](../mfc/reference/cmonthcalctrl-class.md)|`CTime`|Minimalna wartość/maksymalna wartość|
|Kontrolki postępu|msctls_progress32|[CProgressCtrl](../mfc/reference/cprogressctrl-class.md)|None; tylko kontroli|Brak|
|Kontrolka 2 edycji wzbogaconej|RichEdit20A|[CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)|`CString`|Maksymalna liczba znaków|
|Formantu edycji wzbogaconej|RICHEDIT|`CRichEditCtrl`|`CString`|Maksymalna liczba znaków|
|Pasek przewijania (poziomy lub pionowy|PASEK PRZEWIJANIA|[CScrollBar](../mfc/reference/cscrollbar-class.md)|`int`|Minimalna wartość/maksymalna wartość|
|suwak|msctls_trackbar32|[CSliderCtrl](../mfc/reference/csliderctrl-class.md)|`int`|Minimalna wartość/maksymalna wartość|
|Kontrolki pokrętła|msctls_updown32|[CSpinButtonCtrl](../mfc/reference/cspinbuttonctrl-class.md)|None; tylko kontroli|Brak|
|Kontrolki karty|SysTabControl32|[CTabCtrl](../mfc/reference/ctabctrl-class.md)|None; tylko kontroli|Brak|
|Kontrolka drzewa|SysTreeView32|[CTreeCtrl](../mfc/reference/ctreectrl-class.md)|None; tylko kontroli|Brak|

## <a name="see-also"></a>Zobacz też

[Dodawanie zmiennej członkowskiej](../ide/adding-a-member-variable-visual-cpp.md)