---
title: Niszczenie okna dialogowego | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 66a3ef9a72107ffb36a75834a6e197aba394c420
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33343931"
---
# <a name="destroying-the-dialog-box"></a>Niszczenie okna dialogowego
Modalne okna dialogowe są zwykle tworzone w ramce stosu i zniszczone podczas kończenia funkcja, której zostały utworzone. Destruktor obiektu okna dialogowego jest wywoływane, gdy obiekt wykracza poza zakres.  
  
 Niemodalne okna dialogowe są zwykle tworzone i należących do widoku lub ramki okna nadrzędnego — aplikacji główną ramkę okna lub ramki okna dokumentu. Wartość domyślna [OnClose](../mfc/reference/cwnd-class.md#onclose) wywołań obsługi [DestroyWindow](../mfc/reference/cwnd-class.md#destroywindow), który niszczy okna dialogowego. Jeśli okno dialogowe funkcjonował samodzielnie, nie wskaźniki do jego lub inne semantyki specjalne prawa własności, należy zastąpić [PostNcDestroy](../mfc/reference/cwnd-class.md#postncdestroy) zniszczenie obiektu okna dialogowego C++. Należy również zastąpić [OnCancel](../mfc/reference/cdialog-class.md#oncancel) i Wywołaj `DestroyWindow` z wewnątrz. W przeciwnym razie właściciela okna dialogowego należy zniszczyć obiektu języka C++, gdy nie jest już konieczne.  
  
## <a name="see-also"></a>Zobacz też  
 [Cykl życiowy okna dialogowego](../mfc/life-cycle-of-a-dialog-box.md)

