---
title: Niszczenie okna dialogowego | Dokumentacja firmy Microsoft
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
- dialog boxes [MFC], deleting
- destruction, dialog box
- dialog boxes [MFC], destroying
- dialog boxes [MFC], removing
- modeless dialog boxes [MFC], destroying
- MFC dialog boxes [MFC], destroying
- modal dialog boxes [MFC], destroying
ms.assetid: dabceee7-3639-4d85-bf34-73515441b3d0
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0b1b6c94c4c7efe3bc3300d6c8c5c34fbe890fb4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="destroying-the-dialog-box"></a>Niszczenie okna dialogowego
Modalne okna dialogowe są zwykle tworzone w ramce stosu i zniszczone podczas kończenia funkcja, której zostały utworzone. Destruktor obiektu okna dialogowego jest wywoływane, gdy obiekt wykracza poza zakres.  
  
 Niemodalne okna dialogowe są zwykle tworzone i należących do widoku lub ramki okna nadrzędnego — aplikacji główną ramkę okna lub ramki okna dokumentu. Wartość domyślna [OnClose](../mfc/reference/cwnd-class.md#onclose) wywołań obsługi [DestroyWindow](../mfc/reference/cwnd-class.md#destroywindow), który niszczy okna dialogowego. Jeśli okno dialogowe funkcjonował samodzielnie, nie wskaźniki do jego lub inne semantyki specjalne prawa własności, należy zastąpić [PostNcDestroy](../mfc/reference/cwnd-class.md#postncdestroy) zniszczenie obiektu okna dialogowego C++. Należy również zastąpić [OnCancel](../mfc/reference/cdialog-class.md#oncancel) i Wywołaj `DestroyWindow` z wewnątrz. W przeciwnym razie właściciela okna dialogowego należy zniszczyć obiektu języka C++, gdy nie jest już konieczne.  
  
## <a name="see-also"></a>Zobacz też  
 [Cykl życiowy okna dialogowego](../mfc/life-cycle-of-a-dialog-box.md)

