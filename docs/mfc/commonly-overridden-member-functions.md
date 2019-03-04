---
title: Powszechnie zastępowane funkcje członkowskie
ms.date: 11/04/2016
helpviewer_keywords:
- CDialog class [MFC], members
- OnInitDialog function
- dialog classes [MFC], commonly overridden member functions
- OnCancel function
- overriding, dialog class members
- OnOK function
- MFC dialog boxes [MFC], overriding member functions
ms.assetid: 78eb566c-e361-4c86-8db5-c7e2791b249a
ms.openlocfilehash: 26a1527dbdac4b2a9deb57fb13481f8d2f9cb5b7
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57263822"
---
# <a name="commonly-overridden-member-functions"></a>Powszechnie zastępowane funkcje członkowskie

W poniższej tabeli wymieniono najbardziej prawdopodobne funkcje składowe do zastąpienia w swojej `CDialog`-klasy pochodnej.

### <a name="commonly-overridden-member-functions-of-class-cdialog"></a>Powszechnie zastępowane funkcje Członkowskie klasy CDialog

|Funkcja elementu członkowskiego|Komunikat, który odpowiada|Celem zastępowania|
|---------------------|----------------------------|-----------------------------|
|`OnInitDialog`|**/ / ZŁAP**|Zainicjuj formantów okna dialogowego.|
|`OnOK`|**BN_CLICKED** dla przycisku **IDOK**|Należy odpowiedzieć, gdy użytkownik kliknie przycisk OK.|
|`OnCancel`|**BN_CLICKED** dla przycisku **IDCANCEL**|Należy odpowiedzieć, gdy użytkownik kliknie przycisk Anuluj.|

`OnInitDialog`, `OnOK`, i `OnCancel` funkcji wirtualnych. Można je przesłonić, deklarowanie funkcji przez nadrzędne w klasie pochodnej okna dialogowego za pomocą [okno właściwości](/visualstudio/ide/reference/properties-window).

`OnInitDialog` jest wywoływana tuż przed, zostanie wyświetlone okno dialogowe. Wartość domyślna, należy wywołać `OnInitDialog` programu obsługi z przesłonięcia — zwykle jako pierwszą akcją w obsłudze. Domyślnie `OnInitDialog` zwraca **TRUE** do wskazania, że fokus powinna być równa pierwszą kontrolkę w oknie dialogowym.

`OnOK` Zazwyczaj jest wyłączona dla niemodalne, ale nie modalne okna dialogowe. Jeśli ten program obsługi dla modalne okno dialogowe, należy wywołać wersję klasy podstawowej z przesłonięcia — do zapewnienia, że `EndDialog` nosi nazwę — lub zadzwoń `EndDialog` samodzielnie.

`OnCancel` Zazwyczaj jest wyłączona dla Niemodalne okna dialogowe.

Aby uzyskać więcej informacji o tych funkcjach Członkowskich, zobacz klasę [CDialog](../mfc/reference/cdialog-class.md) w *odwołanie MFC* i dyskusji na temat [cykl życiowy okna dialogowego](../mfc/life-cycle-of-a-dialog-box.md).

## <a name="see-also"></a>Zobacz także

[Okna dialogowe](../mfc/dialog-boxes.md)<br/>
[Powszechnie dodawane funkcje składowe](../mfc/commonly-added-member-functions.md)
