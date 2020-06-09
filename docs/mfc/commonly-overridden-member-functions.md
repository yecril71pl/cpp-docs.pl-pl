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
ms.openlocfilehash: 7d4fc9005ff368ef6a83252e8cf0b2005ecf2cef
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619664"
---
# <a name="commonly-overridden-member-functions"></a>Powszechnie zastępowane funkcje członkowskie

W poniższej tabeli wymieniono najbardziej prawdopodobną funkcję członkowską, która ma zostać przesłonięta w `CDialog` klasie pochodnej.

### <a name="commonly-overridden-member-functions-of-class-cdialog"></a>Powszechnie zastępowane funkcje członkowskie klasy CDialog

|Funkcja członkowska|Komunikat, którego dotyczy odpowiedź|Cel przesłonięcia|
|---------------------|----------------------------|-----------------------------|
|`OnInitDialog`|**WM_INITDIALOG**|Zainicjuj kontrolki okna dialogowego.|
|`OnOK`|**BN_CLICKED** przycisku **IDOK**|Reaguj, gdy użytkownik kliknie przycisk OK.|
|`OnCancel`|**BN_CLICKED** przycisku **IDCANCEL**|Reaguj, gdy użytkownik kliknie przycisk Anuluj.|

`OnInitDialog`, `OnOK` , i `OnCancel` są funkcjami wirtualnymi. Aby je zastąpić, należy zadeklarować funkcję zastępującą w klasie dialogu pochodnego za pomocą [kreatora klas MFC](reference/mfc-class-wizard.md).

`OnInitDialog`jest wywoływana tuż przed wyświetleniem okna dialogowego. Musisz wywołać domyślną `OnInitDialog` procedurę obsługi z przesłonięcia — zwykle jako pierwszą akcję w programie obsługi. Domyślnie `OnInitDialog` zwraca **wartość true** , aby wskazać, że fokus powinien być ustawiony na pierwszy formant w oknie dialogowym.

`OnOK`jest zwykle zastępowany dla modalnych okien dialogowych, ale nie dla modalnych. Jeśli zastąpisz tę procedurę obsługi dla modalnego okna dialogowego, wywołaj wersję klasy bazowej z przesłonięcia — aby upewnić się, że `EndDialog` jest wywoływana — lub wywołaj `EndDialog` siebie.

`OnCancel`jest zwykle zastępowany dla niemodalnych okien dialogowych.

Aby uzyskać więcej informacji o tych funkcjach składowych, zobacz klasy [CDialog](reference/cdialog-class.md) w *dokumentacji MFC* i dyskusji na temat [pracy z polami okna dialogowego w MFC](life-cycle-of-a-dialog-box.md).

## <a name="see-also"></a>Zobacz też

[Okna dialogowe](dialog-boxes.md)<br/>
[Powszechnie dodawane funkcje składowe](commonly-added-member-functions.md)
