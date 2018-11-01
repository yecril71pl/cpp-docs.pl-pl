---
title: Klasy przeciągania i upuszczania oraz transferów danych OLE
ms.date: 11/04/2016
f1_keywords:
- vc.classes.ole
helpviewer_keywords:
- ActiveX classes [MFC]
- OLE drag and drop [MFC], and data transfer classes
- drag and drop [MFC], classes
- data transfer [MFC], OLE
- data transfer classes [MFC]
ms.assetid: c8ab2825-ed69-4b88-8ae6-f368b94726b8
ms.openlocfilehash: 7520881314da9568f6130f5fe2ccf0a3e0e88e2a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50475192"
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

