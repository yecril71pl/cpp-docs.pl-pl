---
title: "Formatowanie znaków w formantach edycji wzbogaconej | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- formatting [MFC], characters
- rich edit controls [MFC], character formatting in
- CRichEditCtrl class [MFC], character formatting in
ms.assetid: c80f4305-75ad-45f9-8d17-d83d0fe79be5
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 86b9686396d8f3bd6abd67f5a1f33be0d20bdc16
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="character-formatting-in-rich-edit-controls"></a>Formatowanie znaków w formantach edycji wzbogaconej
Możesz użyć funkcji Członkowskich formantu edycji wzbogaconej ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) do formatowania znaków i pobrać informacji o formatowania. Dla znaków można określić krój, rozmiar, kolor i efekty, takie jak pogrubienie, kursywa, a chronione.  
  
 Można zastosować formatowanie znaków za pomocą [SetSelectionCharFormat](../mfc/reference/cricheditctrl-class.md#setselectioncharformat) i [SetWordCharFormat](../mfc/reference/cricheditctrl-class.md#setwordcharformat) funkcji elementów członkowskich. Aby określić bieżący znak formatowania zaznaczonego tekstu, użyj [GetSelectionCharFormat](../mfc/reference/cricheditctrl-class.md#getselectioncharformat) funkcję elementu członkowskiego. [CHARFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb787881) struktura jest używana z tych funkcji Członkowskich, aby określić atrybuty znaków. Jeden z członków ważne **CHARFORMAT** jest **dwMask**. W `SetSelectionCharFormat` i `SetWordCharFormat`, **dwMask** określa atrybuty znaków zostanie ustawiony przez wywołanie tej funkcji. `GetSelectionCharFormat`Raporty atrybuty pierwszy znak w zaznaczeniu; **dwMask** określa atrybuty, które są spójne w całym zaznaczenia.  
  
 Można również pobieranie i ustawianie "domyślne formatowanie znaków," który jest formatowanie zastosowane do znaków następnie wstawionego. Na przykład jeśli użytkownik wpisze znak aplikacji ustawia domyślny znak formatowania mają zostać pogrubione, ten znak jest pogrubiony. Aby get i set, formatowanie znaków domyślne, należy użyć [GetDefaultCharFormat](../mfc/reference/cricheditctrl-class.md#getdefaultcharformat) i [SetDefaultCharFormat](../mfc/reference/cricheditctrl-class.md#setdefaultcharformat) funkcji elementów członkowskich.  
  
 Atrybut "chronionych" znak nie zmienia wygląd tekstu. Jeśli użytkownik próbuje zmodyfikować chroniony tekst, kontrolki zaawansowanej edycji wysyła jej okna nadrzędnego **EN_PROTECTED** komunikat powiadomienia, dzięki czemu okno nadrzędne umożliwić lub uniemożliwić zmianę. Ten komunikat powiadomienia, należy ją włączyć za pomocą [SetEventMask](../mfc/reference/cricheditctrl-class.md#seteventmask) funkcję elementu członkowskiego. Aby uzyskać więcej informacji na temat maski zdarzeń, zobacz [powiadomienia za pomocą formantu edycji wzbogaconej](../mfc/notifications-from-a-rich-edit-control.md)w dalszej części tego tematu.  
  
 Kolor pierwszego planu jest atrybutem znaku, ale kolor tła jest właściwością kontrolki zaawansowanej edycji. Aby ustawić kolor tła, użyj [SetBackgroundColor](../mfc/reference/cricheditctrl-class.md#setbackgroundcolor) funkcję elementu członkowskiego.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CRichEditCtrl](../mfc/using-cricheditctrl.md)   
 [Formanty](../mfc/controls-mfc.md)

