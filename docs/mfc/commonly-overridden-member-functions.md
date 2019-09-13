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
ms.openlocfilehash: f63dd6079b96181305f3207d4a1ef823df8d8ba4
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907689"
---
# <a name="commonly-overridden-member-functions"></a>Powszechnie zastępowane funkcje członkowskie

W poniższej tabeli wymieniono najbardziej prawdopodobną funkcję członkowską, która `CDialog`ma zostać przesłonięta w klasie pochodnej.

### <a name="commonly-overridden-member-functions-of-class-cdialog"></a>Powszechnie zastępowane funkcje członkowskie klasy CDialog

|Funkcja członkowska|Komunikat, którego dotyczy odpowiedź|Cel przesłonięcia|
|---------------------|----------------------------|-----------------------------|
|`OnInitDialog`|**WM_INITDIALOG**|Zainicjuj kontrolki okna dialogowego.|
|`OnOK`|**BN_CLICKED** przycisku **IDOK**|Reaguj, gdy użytkownik kliknie przycisk OK.|
|`OnCancel`|**BN_CLICKED** przycisku **IDCANCEL**|Reaguj, gdy użytkownik kliknie przycisk Anuluj.|

`OnInitDialog`, `OnOK`, i `OnCancel` są funkcjami wirtualnymi. Aby je zastąpić, należy zadeklarować funkcję zastępującą w klasie dialogu pochodnego za pomocą [kreatora klas MFC](reference/mfc-class-wizard.md).

`OnInitDialog`jest wywoływana tuż przed wyświetleniem okna dialogowego. Musisz wywołać domyślną `OnInitDialog` procedurę obsługi z przesłonięcia — zwykle jako pierwszą akcję w programie obsługi. Domyślnie zwraca `OnInitDialog` **wartość true** , aby wskazać, że fokus powinien być ustawiony na pierwszy formant w oknie dialogowym.

`OnOK`jest zwykle zastępowany dla modalnych okien dialogowych, ale nie dla modalnych. Jeśli zastąpisz tę procedurę obsługi dla modalnego okna dialogowego, wywołaj wersję klasy bazowej z przesłonięcia — `EndDialog` aby upewnić się, `EndDialog` że jest wywoływana — lub wywołaj siebie.

`OnCancel`jest zwykle zastępowany dla niemodalnych okien dialogowych.

Aby uzyskać więcej informacji o tych funkcjach składowych, zobacz Klasa [CDialog](../mfc/reference/cdialog-class.md) w *dokumentacji MFC* i w omówieniu [cyklu życia okna dialogowego](../mfc/life-cycle-of-a-dialog-box.md).

## <a name="see-also"></a>Zobacz także

[Okna dialogowe](../mfc/dialog-boxes.md)<br/>
[Powszechnie dodawane funkcje składowe](../mfc/commonly-added-member-functions.md)
