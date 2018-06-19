---
title: OLE przeciągania i upuszczania oraz transferów danych klasy | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.classes.ole
dev_langs:
- C++
helpviewer_keywords:
- ActiveX classes [MFC]
- OLE drag and drop [MFC], and data transfer classes
- drag and drop [MFC], classes
- data transfer [MFC], OLE
- data transfer classes [MFC]
ms.assetid: c8ab2825-ed69-4b88-8ae6-f368b94726b8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d55d6d171f490631afe17a605f50607fb55f070b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33347045"
---
# <a name="ole-drag-and-drop-and-data-transfer-classes"></a>Klasy przeciągania i upuszczania oraz transferów danych OLE
Te klasy są używane w transferów danych OLE. Umożliwiają one danych transferowanych między aplikacjami za pomocą Schowka lub przeciągania i upuszczania.  
  
 [COleDropSource](../mfc/reference/coledropsource-class.md)  
 Określa operację przeciągania i upuszczania od początku do końca. Ta klasa określa po uruchomieniu operacji przeciągania i po jej zakończeniu. Wyświetla również opinii kursora podczas operacji przeciągania i upuszczania.  
  
 [COleDataSource](../mfc/reference/coledatasource-class.md)  
 Używany, gdy aplikacja udostępnia dane do transferu danych. `COleDataSource` można wyświetlać jako obiekt Schowka zorientowane obiektowo.  
  
 [COleDropTarget](../mfc/reference/coledroptarget-class.md)  
 Reprezentuje element docelowy operacji przeciągania i upuszczania. A `COleDropTarget` obiekt odpowiada okna na ekranie. Określa czy akceptować wszystkie dane na jej i implementuje operacji usuwania rzeczywistych.  
  
 [COleDataObject](../mfc/reference/coledataobject-class.md)  
 Używane jako stronie odbiorcy do `COleDataSource`. `COleDataObject` obiekty zapewniają dostęp do danych przechowywanych przez `COleDataSource` obiektu.  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd klas](../mfc/class-library-overview.md)

