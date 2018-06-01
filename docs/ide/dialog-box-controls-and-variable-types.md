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
ms.openlocfilehash: f2fbae37072f50898181334a9059a7dc9c6a83a9
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2018
ms.locfileid: "33335068"
---
# <a name="dialog-box-controls-and-variable-types"></a>Formanty okna dialogowego i typy zmiennych
Można użyć [Kreator dodawania zmiennej elementu członkowskiego](../ide/add-member-variable-wizard.md) można dodać zmienną członkowską do kontrolka okna dialogowego, utworzone za pomocą MFC. Typ formantu, dla którego można dodać zmiennej członka Określa opcje, które są wyświetlane w oknie dialogowym.  
  
 W poniższej tabeli opisano wszystkie typy okna dialogowego pole formantu, są obsługiwane w MFC i [Edytor okien dialogowych](../windows/dialog-editor.md)i ich dostępnych typów, jak i wartości.  
  
|Formant|Typ formantu|Typ zmiennej formantu|Wartość typu zmiennej|Wartości minimalnej i maksymalnej (tylko typ wartości)|  
|-------------|------------------|---------------------------|-------------------------|-----------------------------------------|  
|Formantu animacji|SysAnimate32|[CAnimateCtrl](../mfc/reference/canimatectrl-class.md)|Brak; tylko kontroli|Brak|  
|Przycisk|PRZYCISK|[CButton](../mfc/reference/cbutton-class.md)|Brak; tylko kontroli|Brak|  
|Pole wyboru|SPRAWDŹ|[CButton](../mfc/reference/cbutton-class.md)|**BOOL**|Wartość minimalna wartość/Maks.|  
|Pola kombi|POLA KOMBI COMBOBOX|[CComboBox](../mfc/reference/ccombobox-class.md)|[Cstring —](../atl-mfc-shared/reference/cstringt-class.md)|Maksymalna liczba znaków|  
|Formant wyboru daty czasu|SysDateTimePick32|[CDateTimeCtrl](../mfc/reference/cdatetimectrl-class.md)|[Ctime —](../atl-mfc-shared/reference/ctime-class.md)|Wartość minimalna wartość/Maks.|  
|pole edycji|EDYTUJ|[CEdit](../mfc/reference/cedit-class.md)|`CString`, int, UINT, long, DWORD, float, double, BYTE, short, BOOL, `COleDateTime`, lub **COleCurrency**|Minimalna wartość/maksymalna wartość; Niektóre znaki max pomocy technicznej|  
|Kontrola skrótu|msctls_hotkey32|[CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)|Brak; tylko kontroli|Brak|  
|pola listy|POLA LISTY|[CListBox](../mfc/reference/clistbox-class.md)|`CString`|Maksymalna liczba znaków|  
|Kontrolki listy|SysListView32|[CListCtrl](../mfc/reference/clistctrl-class.md)|Brak; tylko kontroli|Brak|  
|Kontrolowanie kalendarza miesięcznego|SysMonthCal32|[CMonthCalCtrl](../mfc/reference/cmonthcalctrl-class.md)|`CTime`|Wartość minimalna wartość/Maks.|  
|Formantu postępu|msctls_progress32|[CProgressCtrl](../mfc/reference/cprogressctrl-class.md)|Brak; tylko kontroli|Brak|  
|Kontrolki zaawansowanej edycji 2|RichEdit20A|[CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)|`CString`|Maksymalna liczba znaków|  
|Formantu edycji wzbogaconej|RICHEDIT|`CRichEditCtrl`|`CString`|Maksymalna liczba znaków|  
|Pasek przewijania (pionowy czy poziomy|PASEK PRZEWIJANIA|[CScrollBar](../mfc/reference/cscrollbar-class.md)|`int`|Wartość minimalna wartość/Maks.|  
|suwak|msctls_trackbar32|[CSliderCtrl](../mfc/reference/csliderctrl-class.md)|`int`|Wartość minimalna wartość/Maks.|  
|Pokrętła|msctls_updown32|[CSpinButtonCtrl](../mfc/reference/cspinbuttonctrl-class.md)|Brak; tylko kontroli|Brak|  
|Formantu karty|SysTabControl32|[CTabCtrl](../mfc/reference/ctabctrl-class.md)|Brak; tylko kontroli|Brak|  
|Formant drzewa|SysTreeView32|[CTreeCtrl](../mfc/reference/ctreectrl-class.md)|Brak; tylko kontroli|Brak|  
  
## <a name="see-also"></a>Zobacz też  
 [Dodawanie zmiennej członkowskiej](../ide/adding-a-member-variable-visual-cpp.md)