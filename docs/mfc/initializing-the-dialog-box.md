---
title: Inicjowanie okna dialogowego | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- initializing dialog boxes [MFC]
- OnInitDialog method [MFC]
- modal dialog boxes [MFC], initializing
- modeless dialog boxes [MFC], initializing
- MFC dialog boxes [MFC], initializing
ms.assetid: 968142f5-19f9-4b34-a1d4-8e6412d4379b
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 6568c9bd9002df880a5501dd68e7050a4dc14706
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="initializing-the-dialog-box"></a>Inicjowanie okna dialogowego
Po okna dialogowego pole i wszystkie jego formantów są tworzone, ale przed okno dialogowe zostanie wyświetlone okno (albo typu) na ekranie obiektu okna dialogowego przez [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog) została wywołana funkcja elementu członkowskiego. Modalne okno dialogowe, to wystąpi podczas `DoModal` wywołania. Pola z niemodalnego okna dialogowego `OnInitDialog` jest wywoływane, gdy **Utwórz** jest wywoływana. Zwykle zastąpienie `OnInitDialog` zainicjować formantów okna dialogowego, takie jak ustawianie początkowy tekst pola edycji. Należy wywołać `OnInitDialog` funkcji członkowskiej klasy podstawowej, `CDialog`, z Twojego `OnInitDialog` zastąpienia.  
  
 Jeśli chcesz ustawić kolor tła okna dialogowego (oraz że wszystkie inne okna dialogowe w aplikacji), zobacz [Ustawianie koloru tła okna dialogowego](../mfc/setting-the-dialog-boxs-background-color.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Cykl życiowy okna dialogowego](../mfc/life-cycle-of-a-dialog-box.md)

