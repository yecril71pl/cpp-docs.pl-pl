---
title: Powszechnie zastępowane funkcje Członkowskie | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CDialog class [MFC], members
- OnInitDialog function
- dialog classes [MFC], commonly overridden member functions
- OnCancel function
- overriding, dialog class members
- OnOK function
- MFC dialog boxes [MFC], overriding member functions
ms.assetid: 78eb566c-e361-4c86-8db5-c7e2791b249a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: aabc88db4fcb2a484ca44feea8fcdf7727e23a16
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46431414"
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

## <a name="see-also"></a>Zobacz też

[Okna dialogowe](../mfc/dialog-boxes.md)<br/>
[Powszechnie dodawane funkcje składowe](../mfc/commonly-added-member-functions.md)
