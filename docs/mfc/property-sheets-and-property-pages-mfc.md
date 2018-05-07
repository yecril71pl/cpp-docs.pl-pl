---
title: Arkusze właściwości i strony właściwości (MFC) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC dialog boxes [MFC], tabs
- property pages [MFC], property sheets
- CPropertyPage class [MFC], property sheets and pages
- CPropertySheet class [MFC], property sheets and pages
- property sheets, propert pages
ms.assetid: de8fea12-6c35-4cef-8625-b8073a379446
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 882b2d93ba7938017f64b1ad8fb8e680e0af42db
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="property-sheets-and-property-pages-mfc"></a>Arkusze właściwości i strony właściwości (MFC)
MFC [okno dialogowe](../mfc/dialog-boxes.md) może przybrać "karcie okna dialogowego" wyszukiwania przez włączenie arkusze właściwości i strony właściwości. Tego rodzaju okno dialogowe podobne do wielu okien dialogowych w programie Microsoft Word, Excel i Visual C++ o nazwie "arkusz właściwości" w MFC, prawdopodobnie zawiera stosu arkuszy z kartami, podobnie jak w stosie widoczna od początku do końca lub grupy systemu windows w kaskadowego folderów plików. Formanty na karcie front są widoczne; tylko karcie etykietą jest widoczny na kartach tylnej. Arkusze właściwości są szczególnie użyteczne w przypadku zarządzania dużą liczbą ustawienia dość starannie dzielą się na kilka grup lub właściwości. Zazwyczaj jeden arkusz właściwości można uprościć interfejsu użytkownika, zastępując wiele oddzielnych okien dialogowych.  
  
 Począwszy od wersji 4.0 MFC, arkuszy właściwości strony właściwości są stosowane i używanie formantów wspólnych, które pochodzą z wersji Windows 95 lub Windows NT 3.51 i nowszych.  
  
 Arkusze właściwości są implementowane przy użyciu klasy [cpropertysheet —](../mfc/reference/cpropertysheet-class.md) i [cpropertypage —](../mfc/reference/cpropertypage-class.md) (opisany w *odwołania MFC*). `CPropertySheet` Definiuje ogólną okna dialogowego, które może zawierać wiele "stron" na podstawie `CPropertyPage`.  
  
 Aby uzyskać informacje na temat tworzenia i Praca z arkuszami właściwości, zobacz temat [arkusze właściwości](../mfc/property-sheets-mfc.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Okna dialogowe](../mfc/dialog-boxes.md)   
 [Cykl życiowy okna dialogowego](../mfc/life-cycle-of-a-dialog-box.md)   
 [Arkusze właściwości i strony właściwości w MFC](../mfc/property-sheets-and-property-pages-in-mfc.md)   
 [Wymiana danych](../mfc/exchanging-data.md)   
 [Tworzenie niemodalnego arkusza właściwości](../mfc/creating-a-modeless-property-sheet.md)   
 [Obsługa przycisku Zastosuj](../mfc/handling-the-apply-button.md)

