---
title: "Kontenery formantów ActiveX: Wstawianie formantu do aplikacji kontenera formantów | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- ActiveX control containers [MFC], inserting controls
- ActiveX controls [MFC], adding to projects
ms.assetid: bbb617ff-872f-43d8-b4d6-c49adb16b148
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 3cf288014f47ee1e497ca5a38a3c48368a3b1e6f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="activex-control-containers-inserting-a-control-into-a-control-container-application"></a>Kontenery kontrolek ActiveX: wstawianie kontrolki do aplikacji kontenera kontrolek
Aby formantu ActiveX mógł korzystać z aplikacji kontenera kontrolek ActiveX, należy dodać formantu ActiveX do aplikacji kontenera przy użyciu [Wstawianie formantu ActiveX](../windows/insert-activex-control-dialog-box.md) okno dialogowe.  
  
 Aby dodać kontrolki ActiveX w projekcie kontenera formantu ActiveX, zobacz [wyświetlanie i dodawanie formantów ActiveX do okna dialogowego](../windows/viewing-and-adding-activex-controls-to-a-dialog-box.md).  
  
 Po dodaniu formantu, należy dodać zmienną członkowską (z typu formantu ActiveX) do klasy okno dialogowe. Aby uzyskać więcej informacji dotyczących tej procedury, zobacz [Dodawanie zmiennej elementu członkowskiego](../ide/adding-a-member-variable-visual-cpp.md).  
  
 Po dodaniu zmiennej członkowskiej klasy, określany jako klasa otoki jest automatycznie wygenerowany i dodany do projektu. Ta klasa jest używana jako interfejs między kontenera formantu i osadzonego formantu.  
  
## <a name="see-also"></a>Zobacz też  
 [Kontenery formantów ActiveX](../mfc/activex-control-containers.md)

