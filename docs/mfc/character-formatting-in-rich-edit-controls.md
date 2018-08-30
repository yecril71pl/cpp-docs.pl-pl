---
title: Formatowanie znaków w formantach edycji wzbogaconej | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- formatting [MFC], characters
- rich edit controls [MFC], character formatting in
- CRichEditCtrl class [MFC], character formatting in
ms.assetid: c80f4305-75ad-45f9-8d17-d83d0fe79be5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e7b56570a2821cef3cd2d2676a5260f42bc2ffaf
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43210773"
---
# <a name="character-formatting-in-rich-edit-controls"></a>Formatowanie znaków w formantach edycji wzbogaconej
Można użyć funkcji składowych kontrolki edycji wzbogaconej ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) do formatowania znaków i, aby pobrać informacje o formatowaniu. Znaki można określić krój czcionki, rozmiar, kolor i efektów, takich jak pogrubienie, kursywa, a chronione.  
  
 Można zastosować formatowanie przy użyciu znaków [SetSelectionCharFormat](../mfc/reference/cricheditctrl-class.md#setselectioncharformat) i [SetWordCharFormat](../mfc/reference/cricheditctrl-class.md#setwordcharformat) funkcji elementów członkowskich. Aby określić bieżący znak formatowanie do zaznaczonego tekstu, należy użyć [GetSelectionCharFormat](../mfc/reference/cricheditctrl-class.md#getselectioncharformat) funkcja elementu członkowskiego. [CHARFORMAT](/windows/desktop/api/richedit/ns-richedit-_charformat) struktury jest używany z tych funkcji elementów członkowskich do określenia atrybuty znaków. Jedną z ważnych elementów członkowskich **CHARFORMAT** jest **dwMask**. W `SetSelectionCharFormat` i `SetWordCharFormat`, **dwMask** określa atrybuty znaków zostanie ustawiony przez wywołanie tej funkcji. `GetSelectionCharFormat` Raporty atrybuty pierwszy znak w zaznaczeniu; **dwMask** określa atrybuty, które są spójne zaznaczenia.  
  
 Można również pobieranie i ustawianie "domyślnego znaków formatowania," który jest sformatowanie znaków następnie wstawiono. Na przykład jeśli użytkownik wpisze znak aplikacja ustawia domyślny znak odpowiadający ustawieniom lokalnym pogrubienie, ten znak jest pogrubiony. Aby uzyskać i ustawianie domyślnego formatowania znaków, należy użyć [GetDefaultCharFormat](../mfc/reference/cricheditctrl-class.md#getdefaultcharformat) i [SetDefaultCharFormat](../mfc/reference/cricheditctrl-class.md#setdefaultcharformat) funkcji elementów członkowskich.  
  
 Atrybut "chroniony" znak nie zmienia się wygląd tekstu. Jeśli użytkownik próbuje zmodyfikować chroniony plik tekstowy, kontrolki edycji wzbogaconej wysyła okna nadrzędnego **EN_PROTECTED** komunikat powiadomienia, dzięki czemu okno nadrzędne umożliwić lub uniemożliwić zmiany. Ten komunikat powiadomienia, należy je włączyć za pomocą [seteventmask —](../mfc/reference/cricheditctrl-class.md#seteventmask) funkcja elementu członkowskiego. Aby uzyskać więcej informacji na temat maski zdarzeń, zobacz [powiadomień w kontrolce edycji wzbogaconej](../mfc/notifications-from-a-rich-edit-control.md)w dalszej części tego tematu.  
  
 Kolor pierwszego planu jest atrybutem znaków, ale kolor tła jest właściwość formantu bogatej edycji. Aby ustawić kolor tła, użyj [SetBackgroundColor](../mfc/reference/cricheditctrl-class.md#setbackgroundcolor) funkcja elementu członkowskiego.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CRichEditCtrl](../mfc/using-cricheditctrl.md)   
 [Kontrolki](../mfc/controls-mfc.md)

