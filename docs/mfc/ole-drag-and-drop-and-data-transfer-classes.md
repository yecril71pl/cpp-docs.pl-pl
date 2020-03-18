---
title: Klasy przeciągania i upuszczania oraz transferów danych OLE
ms.date: 11/04/2016
helpviewer_keywords:
- ActiveX classes [MFC]
- OLE drag and drop [MFC], and data transfer classes
- drag and drop [MFC], classes
- data transfer [MFC], OLE
- data transfer classes [MFC]
ms.assetid: c8ab2825-ed69-4b88-8ae6-f368b94726b8
ms.openlocfilehash: 7e01b6d5a7d14e0af4ca760e6e601e91359c8ab1
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447615"
---
# <a name="ole-drag-and-drop-and-data-transfer-classes"></a>Klasy przeciągania i upuszczania oraz transferów danych OLE

Te klasy są używane w transferach danych OLE. Umożliwiają one przesyłanie danych między aplikacjami przy użyciu Schowka lub poprzez przeciąganie i upuszczanie.

[COleDropSource](../mfc/reference/coledropsource-class.md)<br/>
Steruje operacją przeciągania i upuszczania od początku do końca. Ta klasa określa, kiedy rozpocznie się operacja przeciągania, a po jej zakończeniu. Wyświetla również informacje zwrotne kursora podczas operacji przeciągania i upuszczania.

[By uzyskać COleDataSource](../mfc/reference/coledatasource-class.md)<br/>
Używany, gdy aplikacja udostępnia dane do transferu danych. `COleDataSource` można wyświetlić jako obiekt schowka zorientowany obiektowo.

[COleDropTarget](../mfc/reference/coledroptarget-class.md)<br/>
Reprezentuje element docelowy operacji przeciągania i upuszczania. Obiekt `COleDropTarget` odpowiada okno na ekranie. Określa, czy zatwierdzić wszystkie dane, które zostały na nim usunięte, i implementuje rzeczywistą operację usuwania.

[COleDataObject](../mfc/reference/coledataobject-class.md)<br/>
Używane jako strona odbiornika do `COleDataSource`. obiekty `COleDataObject` zapewniają dostęp do danych przechowywanych przez obiekt `COleDataSource`.

## <a name="see-also"></a>Zobacz też

[Przegląd klas](../mfc/class-library-overview.md)
