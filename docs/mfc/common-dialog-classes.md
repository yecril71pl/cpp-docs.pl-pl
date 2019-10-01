---
title: Wspólne klasy okien dialogowych
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
ms.openlocfilehash: d11d0978763d9599b0471a8e994f15a267f7cb8f
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685561"
---
# <a name="common-dialog-classes"></a>Wspólne klasy okien dialogowych

Oprócz klasy [CDialog](../mfc/reference/cdialog-class.md)MFC dostarcza kilka klas pochodnych z `CDialog`, które hermetyzują najczęściej używane okna dialogowe, jak pokazano w poniższej tabeli. Okna dialogowe hermetyzowane są nazywane "typowymi oknami okna dialogowego" i są częścią biblioteki wspólnych okien dialogowych systemu Windows (COMMDLG. DLL). Zasoby szablonu okna dialogowego i kod dla tych klas są dostępne w oknach wspólnych okien dialogowych systemu Windows, które są częścią systemu Windows w wersji 3,1 lub nowszej.

### <a name="common-dialog-classes"></a>Wspólne klasy okien dialogowych

|Klasa dialogu pochodnego|Przeznaczenie|
|--------------------------|-------------|
|[CColorDialog](../mfc/reference/ccolordialog-class.md)|Umożliwia wybór kolorów przez użytkownika.|
|[CFileDialog](../mfc/reference/cfiledialog-class.md)|Umożliwia użytkownikowi wybranie nazwy pliku do otwarcia lub zapisania.|
|[Okno CFindReplaceDialog](../mfc/reference/cfindreplacedialog-class.md)|Umożliwia użytkownikowi zainicjowanie operacji znajdowania lub zamiany w pliku tekstowym.|
|[CFontDialog](../mfc/reference/cfontdialog-class.md)|Umożliwia użytkownikowi określenie czcionki.|
|[CPrintDialog](../mfc/reference/cprintdialog-class.md)|Umożliwia użytkownikowi określenie informacji dotyczących zadania drukowania.|
|[CPrintDialogEx](../mfc/reference/cprintdialogex-class.md)|Arkusz właściwości drukowania systemu Windows.|

Aby uzyskać więcej informacji na temat wspólnych klas okien dialogowych, zobacz nazwy poszczególnych klas w *Kompendium MFC*. MFC dostarcza także szereg standardowych klas okien dialogowych używanych na potrzeby OLE. Aby uzyskać informacje o tych klasach, zobacz Klasa bazowa [COleDialog](../mfc/reference/coledialog-class.md)w *dokumentacji MFC*.

Trzy inne klasy w MFC mają charakterystykę podobną do okna dialogowego. Aby uzyskać informacje na temat klas [CFormView](../mfc/reference/cformview-class.md), [formularzy CRecordView](../mfc/reference/crecordview-class.md)i [CDaoRecordView](../mfc/reference/cdaorecordview-class.md), zobacz klasy w *Kompendium MFC*. Aby uzyskać informacje na temat klasy [CDialogBar](../mfc/reference/cdialogbar-class.md), zobacz [paski okna dialogowego](../mfc/dialog-bars.md).

## <a name="see-also"></a>Zobacz także

[Okna dialogowe](../mfc/dialog-boxes.md)<br/>
[Praca z polami okna dialogowego w MFC](../mfc/life-cycle-of-a-dialog-box.md)<br/>
[Okna dialogowe w OLE](../mfc/dialog-boxes-in-ole.md)
