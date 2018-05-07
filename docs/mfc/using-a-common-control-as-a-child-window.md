---
title: Używanie formantu wspólnego jako okna podrzędnego | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- controls [MFC], using as child windows
- windows [MFC], common controls as
- child windows [MFC], common controls as
- common controls [MFC], child windows
- Windows common controls [MFC], child windows
ms.assetid: 608f7d47-7854-4fce-bde9-856c51e76753
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 50d21675d913211026a2077a0830b7d8ed1225c9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="using-a-common-control-as-a-child-window"></a>Używanie formantu wspólnego jako okna podrzędnego
Wszelkie formanty standardowe systemu Windows może służyć jako okna podrzędnego inne okna. W poniższej procedurze opisano sposób tworzenia formantu wspólnego dynamicznie i następnie pracy z nimi.  
  
### <a name="to-use-a-common-control-as-a-child-window"></a>Aby użyć formantu wspólnego jako okna podrzędnego  
  
1.  Zdefiniuj formantu w klasy pokrewne lub obsługi.  
  
2.  Użyj formantu zastępowania [CWnd::Create](../mfc/reference/cwnd-class.md#create) metodę w celu utworzenia sterowania systemu Windows.  
  
3.  Po utworzeniu formantu (jak wczesne jako `OnCreate` obsługi Jeśli podklasy formantu), można manipulować przy użyciu jego funkcje Członkowskie formantu. Opisy pojedynczych formantów na [formanty](../mfc/controls-mfc.md) szczegółowe informacje na temat metody.  
  
4.  Po zakończeniu za pomocą formantu, użyj [CWnd::DestroyWindow](../mfc/reference/cwnd-class.md#destroywindow) do zniszczenia kontrolki.  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie i używanie formantów](../mfc/making-and-using-controls.md)   
 [Kontrolki](../mfc/controls-mfc.md)

