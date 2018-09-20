---
title: OLE przeciągania i upuszczania oraz transferów danych klas | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: a4b5d694d0081fbe2d852884c4a379e962c22f2a
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46444141"
---
# <a name="ole-drag-and-drop-and-data-transfer-classes"></a>Klasy przeciągania i upuszczania oraz transferów danych OLE

Te klasy są używane w transferów danych OLE. Umożliwiają one danych transferowanych między aplikacjami przy użyciu Schowka lub za pomocą przeciągania i upuszczania.

[COleDropSource](../mfc/reference/coledropsource-class.md)<br/>
Określa operację przeciągania i upuszczania, od początku do końca. Ta klasa określa po rozpoczęciu operacji przeciągania, a kiedy kończy się. Wyświetla również opinii kursora podczas operacji przeciągania i upuszczania.

[COleDataSource](../mfc/reference/coledatasource-class.md)<br/>
Używane, gdy aplikacja udostępnia dane do transferu danych. `COleDataSource` może być wyświetlane jako obiekt Schowka zorientowane obiektowo.

[COleDropTarget](../mfc/reference/coledroptarget-class.md)<br/>
Reprezentuje obiekt docelowy operacji przeciągania i upuszczania. Element `COleDropTarget` obiektu odnosi się do okna na ekranie. Ustala, czy należy zaakceptować wszystkie dane na jego i implementuje operację rzeczywiste listy.

[COleDataObject](../mfc/reference/coledataobject-class.md)<br/>
Używane jako stronie odbiorcy, aby `COleDataSource`. `COleDataObject` obiekty zapewniają dostęp do danych przechowywanych przez `COleDataSource` obiektu.

## <a name="see-also"></a>Zobacz też

[Klasa — Przegląd](../mfc/class-library-overview.md)

