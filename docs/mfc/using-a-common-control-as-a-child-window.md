---
title: "Używanie formantu wspólnego jako okna podrzędnego | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- controls [MFC], using as child windows
- windows [MFC], common controls as
- child windows [MFC], common controls as
- common controls [MFC], child windows
- Windows common controls [MFC], child windows
ms.assetid: 608f7d47-7854-4fce-bde9-856c51e76753
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 116b844f9ecc270d31fe3731c38a63e64b2541fe
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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
 [Formanty](../mfc/controls-mfc.md)

