---
title: Drukowanie w formantach edycji wzbogaconej | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- printing [MFC], CRichEditCtrl
- rich edit controls [MFC], printing
- CRichEditCtrl class [MFC], printing
ms.assetid: dbda0e40-018f-424e-b5d8-7b489aaf27af
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ab8e15e25e2d419bb7c3ac67fc2c6f3453fb03c4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="printing-in-rich-edit-controls"></a>Drukowanie w formantach edycji wzbogaconej
Można ustalić formantów edycji wzbogaconej ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) do renderowania dane wyjściowe dla określonego urządzenia, takie jak drukarka. Można również określić, że urządzenia wyjściowego, dla którego formantu edycji wzbogaconej formatowania tekstu.  
  
 Aby sformatować części zawartości kontrolki edycji wzbogaconej dla określonego urządzenia, można użyć [FormatRange](../mfc/reference/cricheditctrl-class.md#formatrange) funkcję elementu członkowskiego. [FORMATRANGE](http://msdn.microsoft.com/library/windows/desktop/bb787911) struktury używane z tą funkcją określa zakres tekstu do formatowania oraz kontekstu urządzenia (DC) dla urządzenia.  
  
 Po formatowanie tekstu urządzenia wyjściowego, możesz wysłać dane wyjściowe do urządzenia za pomocą [DisplayBand](../mfc/reference/cricheditctrl-class.md#displayband) funkcję elementu członkowskiego. Używając wielokrotnie `FormatRange` i `DisplayBand`, aplikacji, która wyświetla zawartość kontrolki zaawansowanej edycji można zaimplementować pasma. (Pasma jest podział danych wyjściowych na mniejsze części do celów drukowania).  
  
 Można użyć [SetTargetDevice](../mfc/reference/cricheditctrl-class.md#settargetdevice) funkcji członkowskiej, aby określić urządzenie docelowe, dla którego formantu edycji wzbogaconej formatowania tekstu. Ta funkcja jest przydatna do WYSIWYG (widoczna jest możesz uzyskać) formatowania, w którym aplikacja umieszcza tekst przy użyciu drukarki domyślnej czcionki metryki zamiast ekranu.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CRichEditCtrl](../mfc/using-cricheditctrl.md)   
 [Kontrolki](../mfc/controls-mfc.md)

