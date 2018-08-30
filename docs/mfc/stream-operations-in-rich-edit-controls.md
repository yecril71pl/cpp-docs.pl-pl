---
title: Stream operacji w formantach edycji wzbogaconej | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CRichEditCtrl class [MFC], stream operations
- CRichEditCtrl class [MFC], stream storage
- rich edit controls [MFC], stream operations
- storage, stream in CRichEditCtrl
- stream operations in CRichEditCtrl
- stream storage and CRichEditCtrl
ms.assetid: 110b4684-1e76-4ca6-9ef0-5bc8b2d93c78
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f418156fb5be4837bc0dbe9b05b3ad26d7ac02dd
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43196861"
---
# <a name="stream-operations-in-rich-edit-controls"></a>Operacje strumieniowe w formantach edycji wzbogaconej
Można użyć strumieni na przesyłanie danych do lub z kontrolki edycji wzbogaconej ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)). Strumień jest definiowany przez [EDITSTREAM](/windows/desktop/api/richedit/ns-richedit-_editstream) struktury, która określa buforu i zdefiniowanych przez aplikację funkcji wywołania zwrotnego.  
  
 Do odczytywania danych do zaawansowane Edytuj kontrolkę (oznacza to, przesyłanie strumieniowe danych), użyj [StreamIn](../mfc/reference/cricheditctrl-class.md#streamin) funkcja elementu członkowskiego. Kontrolka wywołuje wielokrotnie zdefiniowany przez aplikację funkcji wywołania zwrotnego, który przenosi część danych w buforze każdorazowo.  
  
 Zapisz formant edycji zawartości Zaawansowane (czyli przesyłać strumieniowo dane wyjściowe), możesz użyć [StreamOut](../mfc/reference/cricheditctrl-class.md#streamout) funkcja elementu członkowskiego. Kontrolka wielokrotnie zapisuje do buforu, a następnie wywołuje zdefiniowane przez aplikację funkcji wywołania zwrotnego. Dla każdego wywołania funkcji wywołania zwrotnego zapisuje zawartość buforu.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CRichEditCtrl](../mfc/using-cricheditctrl.md)   
 [Kontrolki](../mfc/controls-mfc.md)

