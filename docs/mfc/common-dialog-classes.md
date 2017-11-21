---
title: "Klasy wspólnych okien dialogowych | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
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
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 50adbc6faa802802c36e18c614992341def06331
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="common-dialog-classes"></a>Klasy wspólnych okien dialogowych
Oprócz klasy [cdialog —](../mfc/reference/cdialog-class.md), MFC udostępnia kilka klas pochodnych `CDialog` które hermetyzują często używane okien dialogowych, jak pokazano w poniższej tabeli. Okna dialogowe hermetyzowany są nazywane "wspólnych okien dialogowych" i są częścią Biblioteka okna dialogowego wspólne systemu Windows (pliku COMMDLG. BIBLIOTEKI DLL). Zasoby szablonu okna dialogowego i kod dla tych klas są udostępniane w oknach wspólnych okien dialogowych, które są częścią systemu Windows w wersji 3.1 lub nowszej.  
  
### <a name="common-dialog-classes"></a>Klasy wspólnych okien dialogowych  
  
|Klasy pochodne okien dialogowych|Cel|  
|--------------------------|-------------|  
|[CColorDialog](../mfc/reference/ccolordialog-class.md)|Umożliwia kolorów wybierz użytkownika.|  
|[CFileDialog](../mfc/reference/cfiledialog-class.md)|Umożliwia użytkownikowi wybranie nazwy pliku, aby otworzyć lub zapisać.|  
|[CFindReplaceDialog](../mfc/reference/cfindreplacedialog-class.md)|Umożliwia użytkownikowi zainicjować Znajdź lub zamienianie operacji w pliku tekstowym.|  
|[CFontDialog](../mfc/reference/cfontdialog-class.md)|Umożliwia użytkownikowi określenie czcionki.|  
|[CPrintDialog](../mfc/reference/cprintdialog-class.md)|Umożliwia użytkownikowi określenie informacje dotyczące zadania drukowania.|  
|[CPrintDialogEx](../mfc/reference/cprintdialogex-class.md)|Arkusz właściwości wydruku systemu Windows 2000.|  
  
 Aby uzyskać więcej informacji na temat klasy wspólnych okien dialogowych, zobacz nazwy poszczególnych klas *odwołania MFC*. MFC udostępnia również liczbę standardowe okno dialogowe klasy służące do OLE. Klasa podstawowa dla informacji o tych klas, [COleDialog](../mfc/reference/coledialog-class.md)w *odwołania MFC*.  
  
 Trzy innych klas MFC mają podobne okno dialogowe właściwości. Aby uzyskać informacje o klasach [CFormView](../mfc/reference/cformview-class.md), [CRecordView](../mfc/reference/crecordview-class.md), i [CDaoRecordView](../mfc/reference/cdaorecordview-class.md), zobacz klas w *dokumentacja MFC*. Aby uzyskać informacje o klasie [cdialogbar —](../mfc/reference/cdialogbar-class.md), zobacz [paski dialogowe](../mfc/dialog-bars.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Okna dialogowe](../mfc/dialog-boxes.md)   
 [Cykl życiowy okna dialogowego](../mfc/life-cycle-of-a-dialog-box.md)   
 [Okna dialogowe w OLE](../mfc/dialog-boxes-in-ole.md)

