---
title: "OLE przeciągania i upuszczania oraz transferów danych klasy | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.classes.ole
dev_langs: C++
helpviewer_keywords:
- ActiveX classes [MFC]
- OLE drag and drop [MFC], and data transfer classes
- drag and drop [MFC], classes
- data transfer [MFC], OLE
- data transfer classes [MFC]
ms.assetid: c8ab2825-ed69-4b88-8ae6-f368b94726b8
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 6bbb1f638de627f4202b30754f6748756418aca6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="ole-drag-and-drop-and-data-transfer-classes"></a>Klasy przeciągania i upuszczania oraz transferów danych OLE
Te klasy są używane w transferów danych OLE. Umożliwiają one danych transferowanych między aplikacjami za pomocą Schowka lub przeciągania i upuszczania.  
  
 [COleDropSource](../mfc/reference/coledropsource-class.md)  
 Określa operację przeciągania i upuszczania od początku do końca. Ta klasa określa po uruchomieniu operacji przeciągania i po jej zakończeniu. Wyświetla również opinii kursora podczas operacji przeciągania i upuszczania.  
  
 [COleDataSource](../mfc/reference/coledatasource-class.md)  
 Używany, gdy aplikacja udostępnia dane do transferu danych. `COleDataSource`można wyświetlać jako obiekt Schowka zorientowane obiektowo.  
  
 [COleDropTarget](../mfc/reference/coledroptarget-class.md)  
 Reprezentuje element docelowy operacji przeciągania i upuszczania. A `COleDropTarget` obiekt odpowiada okna na ekranie. Określa czy akceptować wszystkie dane na jej i implementuje operacji usuwania rzeczywistych.  
  
 [COleDataObject](../mfc/reference/coledataobject-class.md)  
 Używane jako stronie odbiorcy do `COleDataSource`. `COleDataObject`obiekty zapewniają dostęp do danych przechowywanych przez `COleDataSource` obiektu.  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd klas](../mfc/class-library-overview.md)

