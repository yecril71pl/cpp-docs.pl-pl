---
title: 'Kontenery formantów ActiveX: Wstawianie formantu do aplikacji kontenera formantów | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ActiveX control containers [MFC], inserting controls
- ActiveX controls [MFC], adding to projects
ms.assetid: bbb617ff-872f-43d8-b4d6-c49adb16b148
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 716c045fc10b4dd5f3dede20a233d958e669bbd7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33346340"
---
# <a name="activex-control-containers-inserting-a-control-into-a-control-container-application"></a>Kontenery kontrolek ActiveX: wstawianie kontrolki do aplikacji kontenera kontrolek
Aby formantu ActiveX mógł korzystać z aplikacji kontenera kontrolek ActiveX, należy dodać formantu ActiveX do aplikacji kontenera przy użyciu [Wstawianie formantu ActiveX](../windows/insert-activex-control-dialog-box.md) okno dialogowe.  
  
 Aby dodać kontrolki ActiveX w projekcie kontenera formantu ActiveX, zobacz [wyświetlanie i dodawanie formantów ActiveX do okna dialogowego](../windows/viewing-and-adding-activex-controls-to-a-dialog-box.md).  
  
 Po dodaniu formantu, należy dodać zmienną członkowską (z typu formantu ActiveX) do klasy okno dialogowe. Aby uzyskać więcej informacji dotyczących tej procedury, zobacz [Dodawanie zmiennej elementu członkowskiego](../ide/adding-a-member-variable-visual-cpp.md).  
  
 Po dodaniu zmiennej członkowskiej klasy, określany jako klasa otoki jest automatycznie wygenerowany i dodany do projektu. Ta klasa jest używana jako interfejs między kontenera formantu i osadzonego formantu.  
  
## <a name="see-also"></a>Zobacz też  
 [Kontenery kontrolek ActiveX](../mfc/activex-control-containers.md)

