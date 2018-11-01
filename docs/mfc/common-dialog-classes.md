---
title: Klasy wspólnych okien dialogowych
ms.date: 11/04/2016
helpviewer_keywords:
- dialog classes [MFC]
- dialog boxes [MFC], Windows common dialogs
- common dialog boxes [MFC], common dialog classes
- common dialog classes [MFC]
- MFC dialog boxes [MFC], Windows common dialogs
- Windows common dialogs [MFC]
- dialog classes [MFC], common
- common dialog boxes [MFC]
ms.assetid: 5c4f6443-896c-4b05-a7df-8169fdadc71d
ms.openlocfilehash: 9e0ee68970b9ee3255ae72699dc185fc5de5a0f7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50577242"
---
# <a name="common-dialog-classes"></a>Klasy wspólnych okien dialogowych

Oprócz klas [CDialog](../mfc/reference/cdialog-class.md), MFC dostarcza kilka klas pochodnych `CDialog` powszechnie używane okien dialogowych, które hermetyzują, jak pokazano w poniższej tabeli. Okna dialogowe hermetyzowane są nazywane "wspólne okna dialogowe" i są częścią Windows wspólna biblioteka okna dialogowego (pliku COMMDLG. BIBLIOTEKA DLL). Zasoby szablonu okna dialogowego i kod dla tych klas są udostępniane w Windows wspólne okna dialogowe, które są częścią Windows w wersji 3.1 lub nowszej.

### <a name="common-dialog-classes"></a>Klasy wspólnych okien dialogowych

|Klasy pochodne okien dialogowych|Cel|
|--------------------------|-------------|
|[CColorDialog](../mfc/reference/ccolordialog-class.md)|Informuje użytkownika, wybierz opcję kolorów.|
|[CFileDialog](../mfc/reference/cfiledialog-class.md)|Umożliwia użytkownikowi wybranie nazwy pliku, aby otworzyć lub zapisać.|
|[CFindReplaceDialog](../mfc/reference/cfindreplacedialog-class.md)|Umożliwia użytkownikowi zainicjować Znajdź lub Zamień operacji w pliku tekstowym.|
|[CFontDialog](../mfc/reference/cfontdialog-class.md)|Umożliwia użytkownikowi określenie czcionki.|
|[CPrintDialog](../mfc/reference/cprintdialog-class.md)|Pozwala określić informacje dotyczące zadania drukowania użytkownika.|
|[CPrintDialogEx](../mfc/reference/cprintdialogex-class.md)|Arkusz własności drukowania Windows.|

Aby uzyskać więcej informacji na temat klasy wspólnych okien dialogowych Zobacz nazwy poszczególnych klas w *odwołanie MFC*. MFC udostępnia również wiele klas standardowe okno dialogowe, używanych dla mechanizmu OLE. Klasa bazowa dla informacji o tych klas, [COleDialog](../mfc/reference/coledialog-class.md)w *odwołanie MFC*.

Trzy klasy w MFC mają podobne okno dialogowe właściwości. Aby uzyskać informacje o klasach [CFormView](../mfc/reference/cformview-class.md), [CRecordView](../mfc/reference/crecordview-class.md), i [CDaoRecordView](../mfc/reference/cdaorecordview-class.md), patrz klasy w *odwołanie MFC*. Aby uzyskać informacje o klasie [CDialogBar](../mfc/reference/cdialogbar-class.md), zobacz [paski dialogowe](../mfc/dialog-bars.md).

## <a name="see-also"></a>Zobacz też

[Okna dialogowe](../mfc/dialog-boxes.md)<br/>
[Cykl życiowy okna dialogowego](../mfc/life-cycle-of-a-dialog-box.md)<br/>
[Okna dialogowe w OLE](../mfc/dialog-boxes-in-ole.md)

