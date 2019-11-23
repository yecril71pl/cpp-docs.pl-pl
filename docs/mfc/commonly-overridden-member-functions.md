---
title: Powszechnie zastępowane funkcje członkowskie
ms.date: 09/06/2019
helpviewer_keywords:
- CDialog class [MFC], members
- OnInitDialog function
- dialog classes [MFC], commonly overridden member functions
- OnCancel function
- overriding, dialog class members
- OnOK function
- MFC dialog boxes [MFC], overriding member functions
ms.assetid: 78eb566c-e361-4c86-8db5-c7e2791b249a
ms.openlocfilehash: 51a647bb50415af71d6d148d3139f906f503ee2a
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685822"
---
# <a name="commonly-overridden-member-functions"></a>Powszechnie zastępowane funkcje członkowskie

W poniższej tabeli wymieniono najbardziej prawdopodobną funkcję członkowską do przesłonięcia w klasie pochodnej `CDialog`.

### <a name="commonly-overridden-member-functions-of-class-cdialog"></a>Powszechnie zastępowane funkcje członkowskie klasy CDialog

|Funkcja członkowska|Komunikat, którego dotyczy odpowiedź|Cel przesłonięcia|
|---------------------|----------------------------|-----------------------------|
|`OnInitDialog`|**WM_INITDIALOG**|Zainicjuj kontrolki okna dialogowego.|
|`OnOK`|**BN_CLICKED** przycisku **IDOK**|Reaguj, gdy użytkownik kliknie przycisk OK.|
|`OnCancel`|**BN_CLICKED** przycisku **IDCANCEL**|Reaguj, gdy użytkownik kliknie przycisk Anuluj.|

`OnInitDialog`, `OnOK`i `OnCancel` są funkcjami wirtualnymi. Aby je zastąpić, należy zadeklarować funkcję zastępującą w klasie dialogu pochodnego za pomocą [kreatora klas MFC](reference/mfc-class-wizard.md).

`OnInitDialog` jest wywoływana tuż przed wyświetleniem okna dialogowego. Musisz wywołać domyślną procedurę obsługi `OnInitDialog` z przesłonięcia — zazwyczaj jako pierwszą akcję w programie obsługi. Domyślnie `OnInitDialog` zwraca **wartość true** , aby wskazać, że fokus powinien być ustawiony na pierwszy formant w oknie dialogowym.

`OnOK` jest zwykle zastępowany dla modalnych okien dialogowych, ale nie modalnych. Jeśli zastąpisz tę procedurę obsługi dla modalnego okna dialogowego, wywołaj wersję klasy bazowej z przesłonięcia, aby upewnić się, że `EndDialog` jest wywoływana — lub wywołaj `EndDialog` samodzielnie.

`OnCancel` jest zwykle zastępowany dla niemodalnych okien dialogowych.

Aby uzyskać więcej informacji o tych funkcjach składowych, zobacz klasy [CDialog](../mfc/reference/cdialog-class.md) w *dokumentacji MFC* i dyskusji na temat [pracy z polami okna dialogowego w MFC](../mfc/life-cycle-of-a-dialog-box.md).

## <a name="see-also"></a>Zobacz także

[Okna dialogowe](../mfc/dialog-boxes.md)<br/>
[Powszechnie dodawane funkcje składowe](../mfc/commonly-added-member-functions.md)
