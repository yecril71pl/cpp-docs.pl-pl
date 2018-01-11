---
title: Operacje w formantach edycji wzbogaconej strumienia | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- CRichEditCtrl class [MFC], stream operations
- CRichEditCtrl class [MFC], stream storage
- rich edit controls [MFC], stream operations
- storage, stream in CRichEditCtrl
- stream operations in CRichEditCtrl
- stream storage and CRichEditCtrl
ms.assetid: 110b4684-1e76-4ca6-9ef0-5bc8b2d93c78
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c1a73790124adbc1ff8a89290bf4e1d7a4fa6824
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="stream-operations-in-rich-edit-controls"></a>Operacje strumieniowe w formantach edycji wzbogaconej
Strumienie służy do przesyłania danych do lub wychodzący kontrolki edycji wzbogaconej ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)). Strumień jest definiowana za pomocą [EDITSTREAM](http://msdn.microsoft.com/library/windows/desktop/bb787891) struktury, która określa buforu i zdefiniowanym przez aplikację funkcja wywołania zwrotnego.  
  
 Aby odczytać formantów edycji wzbogaconej dane (to znaczy strumienia danych), użyj [StreamIn](../mfc/reference/cricheditctrl-class.md#streamin) funkcji członkowskiej. Kontrolka wywołuje wielokrotnie zdefiniowane przez aplikację funkcja wywołania zwrotnego, który przenosi część danych w buforze zawsze.  
  
 Aby zapisać formant edycji wzbogaconej zawartość (to znaczy strumienia danych wychodzących), można użyć [StreamOut](../mfc/reference/cricheditctrl-class.md#streamout) funkcji członkowskiej. Kontrolki wielokrotnie zapisuje do buforu, a następnie wywołuje funkcję wywołania zwrotnego z określonym przez aplikację. Dla każdego wywołania funkcji wywołania zwrotnego zapisuje zawartość buforu.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CRichEditCtrl](../mfc/using-cricheditctrl.md)   
 [Kontrolki](../mfc/controls-mfc.md)

