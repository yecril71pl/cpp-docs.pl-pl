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
ms.openlocfilehash: ed090057394c385dd12825864c5de9ff7d079e29
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="commonly-overridden-member-functions"></a>Powszechnie zastępowane funkcje członkowskie
W poniższej tabeli wymieniono najbardziej prawdopodobne funkcje Członkowskie do przesłonięcia w Twojej `CDialog`-klasy.  
  
### <a name="commonly-overridden-member-functions-of-class-cdialog"></a>Powszechnie zastępowane funkcje Członkowskie cdialog — klasa  
  
|Funkcja członkowska|Komunikat, który odpowiada|Celem zastąpienia|  
|---------------------|----------------------------|-----------------------------|  
|`OnInitDialog`|**WM_INITDIALOG**|Zainicjuj formanty okna dialogowego.|  
|`OnOK`|**BN_CLICKED** dla przycisku **IDOK**|Odpowiedz, gdy użytkownik kliknie przycisk OK.|  
|`OnCancel`|**BN_CLICKED** dla przycisku **IDCANCEL**|Odpowiedz, gdy użytkownik kliknie przycisk Anuluj.|  
  
 `OnInitDialog`, `OnOK`, i `OnCancel` są funkcje wirtualne. Aby je zastąpić, zastępowanie funkcja zadeklarować w klasie pochodnej okna dialogowego za pomocą [okna właściwości](/visualstudio/ide/reference/properties-window).  
  
 `OnInitDialog` jest wywoływana tuż przed wyświetleniem okna dialogowego. Należy wywołać domyślnie `OnInitDialog` programu obsługi z zastąpienia — zwykle jako pierwszą akcją w obsłudze. Domyślnie `OnInitDialog` zwraca **TRUE** aby wskazać, że należy ustawić fokus do pierwszego formantu w oknie dialogowym.  
  
 `OnOK` Zazwyczaj jest wyłączona dla niemodalne, ale nie modalnych okien dialogowych. Razie przesłonięcia tej obsługi dla modalne okno dialogowe, wywołaj wersja klasy podstawowej z zastąpienia — do zapewnienia, że `EndDialog` jest nazywany — lub zadzwoń `EndDialog` samodzielnie.  
  
 `OnCancel` Zazwyczaj jest wyłączona dla Niemodalne okna dialogowe.  
  
 Aby uzyskać więcej informacji o tych funkcjach Członkowskich zawiera klasa [cdialog —](../mfc/reference/cdialog-class.md) w *odwołania MFC* i dyskusji na [cykl życiowy okna dialogowego](../mfc/life-cycle-of-a-dialog-box.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Okna dialogowe](../mfc/dialog-boxes.md)   
 [Powszechnie dodawane funkcje składowe](../mfc/commonly-added-member-functions.md)
