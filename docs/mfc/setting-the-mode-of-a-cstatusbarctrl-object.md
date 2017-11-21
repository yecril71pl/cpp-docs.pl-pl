---
title: Ustawianie trybu obiektu CStatusBarCtrl | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CStatusBarCtrl
dev_langs: C++
helpviewer_keywords:
- simple mode and status bar controls
- IsSimple method, using
- SetSimple method [MFC]
- status bar controls [MFC], simple and nonsimple modes
- non-simple mode and status bar controls
- CStatusBarCtrl class [MFC], simple and nonsimple modes
ms.assetid: ca6076e5-1501-4e33-8d35-9308941e46c0
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 35f48a87a0b9526ad6150a700190f4509e1128d5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="setting-the-mode-of-a-cstatusbarctrl-object"></a>Ustawianie trybu obiektu CStatusBarCtrl
Istnieją dwa tryby `CStatusBarCtrl` obiektu: proste i prostymi. W większości przypadków formantu paska stanu będzie mieć jeden lub więcej części, wraz z tekstu i prawdopodobnie ikony lub ikony. Jest to tryb prostymi. Aby uzyskać więcej informacji na ten tryb, zobacz [inicjowanie części obiektu CStatusBarCtrl](../mfc/initializing-the-parts-of-a-cstatusbarctrl-object.md).  
  
 Istnieją jednak przypadki, w którym wystarczy do wyświetlania pojedynczy wiersz tekstu. W takim przypadku tryb prosty jest wystarczająca do własnych potrzeb. Aby zmienić tryb `CStatusBarCtrl` obiektu prosty, wywoływania [SetSimple](../mfc/reference/cstatusbarctrl-class.md#setsimple) funkcję elementu członkowskiego. Po umieszczeniu formantu paska stanu w tryb prosty tekst ustawiony przez wywołanie **SetText** funkcji członkowskiej, przekazując 255 jako wartość **nPane** parametru.  
  
 Można użyć [IsSimple](../mfc/reference/cstatusbarctrl-class.md#issimple) funkcji, aby ustalić, jakie tryb `CStatusBarCtrl` jest obiekt.  
  
> [!NOTE]
>  Jeśli obiekt paska stanu został zmieniony z nonsimple prosty lub odwrotnie, natychmiast rysowane jest okno i, jeśli ma to zastosowanie, wszystkie części zdefiniowanych automatycznie zostaną przywrócone.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)   
 [Formanty](../mfc/controls-mfc.md)

