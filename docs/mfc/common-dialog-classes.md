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
ms.openlocfilehash: 2efe095a6d5b71321cbbe56fdee662509baa4573
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619023"
---
# <a name="common-dialog-classes"></a>Klasy wspólnych okien dialogowych

Oprócz klasy [CDialog](reference/cdialog-class.md), MFC dostarcza kilka klas pochodzących od `CDialog` tego, które hermetyzują najczęściej używane okna dialogowe, jak pokazano w poniższej tabeli. Okna dialogowe hermetyzowane są nazywane "typowymi oknami okna dialogowego" i są częścią biblioteki wspólnych okien dialogowych systemu Windows (COMMDLG. DLL). Zasoby szablonu okna dialogowego i kod dla tych klas są dostępne w oknach wspólnych okien dialogowych systemu Windows, które są częścią systemu Windows w wersji 3,1 lub nowszej.

### <a name="common-dialog-classes"></a>Klasy wspólnych okien dialogowych

|Klasa dialogu pochodnego|Przeznaczenie|
|--------------------------|-------------|
|[CColorDialog](reference/ccolordialog-class.md)|Umożliwia wybór kolorów przez użytkownika.|
|[CFileDialog](reference/cfiledialog-class.md)|Umożliwia użytkownikowi wybranie nazwy pliku do otwarcia lub zapisania.|
|[Okno CFindReplaceDialog](reference/cfindreplacedialog-class.md)|Umożliwia użytkownikowi zainicjowanie operacji znajdowania lub zamiany w pliku tekstowym.|
|[CFontDialog](reference/cfontdialog-class.md)|Umożliwia użytkownikowi określenie czcionki.|
|[CPrintDialog](reference/cprintdialog-class.md)|Umożliwia użytkownikowi określenie informacji dotyczących zadania drukowania.|
|[CPrintDialogEx](reference/cprintdialogex-class.md)|Arkusz właściwości drukowania systemu Windows.|

Aby uzyskać więcej informacji na temat wspólnych klas okien dialogowych, zobacz nazwy poszczególnych klas w *Kompendium MFC*. MFC dostarcza także szereg standardowych klas okien dialogowych używanych na potrzeby OLE. Aby uzyskać informacje o tych klasach, zobacz Klasa bazowa [COleDialog](reference/coledialog-class.md)w *dokumentacji MFC*.

Trzy inne klasy w MFC mają charakterystykę podobną do okna dialogowego. Aby uzyskać informacje na temat klas [CFormView](reference/cformview-class.md), [formularzy CRecordView](reference/crecordview-class.md)i [CDaoRecordView](reference/cdaorecordview-class.md), zobacz klasy w *Kompendium MFC*. Aby uzyskać informacje na temat klasy [CDialogBar](reference/cdialogbar-class.md), zobacz [paski okna dialogowego](dialog-bars.md).

## <a name="see-also"></a>Zobacz też

[Okna dialogowe](dialog-boxes.md)<br/>
[Praca z oknami dialogowymi w MFC](life-cycle-of-a-dialog-box.md)<br/>
[Okna dialogowe w OLE](dialog-boxes-in-ole.md)
