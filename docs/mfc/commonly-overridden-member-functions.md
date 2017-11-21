---
title: "Powszechnie zastępowane funkcje Członkowskie | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- CDialog class [MFC], members
- OnInitDialog function
- dialog classes [MFC], commonly overridden member functions
- OnCancel function
- overriding, dialog class members
- OnOK function
- MFC dialog boxes [MFC], overriding member functions
ms.assetid: 78eb566c-e361-4c86-8db5-c7e2791b249a
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 1b5c5c4d5689c57f02766f2d6c2af2ddad88ee1e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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
  
 `OnInitDialog`jest wywoływana tuż przed wyświetleniem okna dialogowego. Należy wywołać domyślnie `OnInitDialog` programu obsługi z zastąpienia — zwykle jako pierwszą akcją w obsłudze. Domyślnie `OnInitDialog` zwraca **TRUE** aby wskazać, że należy ustawić fokus do pierwszego formantu w oknie dialogowym.  
  
 `OnOK`Zazwyczaj jest wyłączona dla niemodalne, ale nie modalnych okien dialogowych. Razie przesłonięcia tej obsługi dla modalne okno dialogowe, wywołaj wersja klasy podstawowej z zastąpienia — do zapewnienia, że `EndDialog` jest nazywany — lub zadzwoń `EndDialog` samodzielnie.  
  
 `OnCancel`Zazwyczaj jest wyłączona dla Niemodalne okna dialogowe.  
  
 Aby uzyskać więcej informacji o tych funkcjach Członkowskich zawiera klasa [cdialog —](../mfc/reference/cdialog-class.md) w *odwołania MFC* i dyskusji na [cykl życiowy okna dialogowego](../mfc/life-cycle-of-a-dialog-box.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Okna dialogowe](../mfc/dialog-boxes.md)   
 [Powszechnie dodawane funkcje Członkowskie](../mfc/commonly-added-member-functions.md)
