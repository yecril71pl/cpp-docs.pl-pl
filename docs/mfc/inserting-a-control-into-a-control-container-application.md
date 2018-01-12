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
ms.workload: cplusplus
ms.openlocfilehash: a1eaaf0426726f252fc4990f06faa73b0598cfbb
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="activex-control-containers-inserting-a-control-into-a-control-container-application"></a>Kontenery kontrolek ActiveX: wstawianie kontrolki do aplikacji kontenera kontrolek
Aby formantu ActiveX mógł korzystać z aplikacji kontenera kontrolek ActiveX, należy dodać formantu ActiveX do aplikacji kontenera przy użyciu [Wstawianie formantu ActiveX](../windows/insert-activex-control-dialog-box.md) okno dialogowe.  
  
 Aby dodać kontrolki ActiveX w projekcie kontenera formantu ActiveX, zobacz [wyświetlanie i dodawanie formantów ActiveX do okna dialogowego](../windows/viewing-and-adding-activex-controls-to-a-dialog-box.md).  
  
 Po dodaniu formantu, należy dodać zmienną członkowską (z typu formantu ActiveX) do klasy okno dialogowe. Aby uzyskać więcej informacji dotyczących tej procedury, zobacz [Dodawanie zmiennej elementu członkowskiego](../ide/adding-a-member-variable-visual-cpp.md).  
  
 Po dodaniu zmiennej członkowskiej klasy, określany jako klasa otoki jest automatycznie wygenerowany i dodany do projektu. Ta klasa jest używana jako interfejs między kontenera formantu i osadzonego formantu.  
  
## <a name="see-also"></a>Zobacz też  
 [Kontenery kontrolek ActiveX](../mfc/activex-control-containers.md)

