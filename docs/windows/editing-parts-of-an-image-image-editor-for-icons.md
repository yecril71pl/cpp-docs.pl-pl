---
title: "Edytowanie części obrazu (edytor obrazów dla ikon) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- Image editor [C++], editing images
- Clipboard [C++], pasting
- images [C++], editing
- images [C++], deleting selected parts
- images [C++], copying selected parts
- images [C++], moving selected parts
- images [C++], dragging and replicating selected parts
- images [C++], pasting into
- graphics [C++], editing
ms.assetid: ff4f5fef-71a4-4fd8-825e-049399fed391
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 4018f3816c75333fd8020c2856ab2538bf54bf1a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="editing-parts-of-an-image-image-editor-for-icons"></a>Edytowanie części obrazu (Edytor obrazów dla ikon)
Można wykonywać operacje edycji standard — wycinanie, kopiowanie, czyszczenia i przenoszenie — na [wybór](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md), czy zaznaczenie jest całego obrazu lub tylko jego części. Ponieważ edytor obrazów używa Schowka systemu Windows, można przenieść obrazów między edytor obrazów i inne aplikacje dla systemu Windows.  
  
 Ponadto można zmienić zaznaczenia, czy zawiera on całego obrazu lub tylko części.  
  
### <a name="to-cut-the-current-selection-and-move-it-to-the-clipboard"></a>Aby wyciąć bieżące zaznaczenie i przenieś go do Schowka  
  
1.  Kliknij przycisk **Wytnij** na **Edytuj** menu.  
  
### <a name="to-copy-the-selection"></a>Aby skopiować zaznaczenie  
  
1.  Umieść wskaźnik wewnątrz obramowanie wyboru lub w dowolnym miejscu na nim, oprócz uchwytów zmiany rozmiaru.  
  
2.  Naciśnij i przytrzymaj **CTRL** klucza, przeciągnij zaznaczenie do nowej lokalizacji. Obszar oryginalnego zaznaczenia jest bez zmian.  
  
3.  Aby skopiować zaznaczenie do obrazu w jego bieżącej lokalizacji, kliknij poza kursor wyboru.  
  
### <a name="to-paste-the-clipboard-contents-into-an-image"></a>Wklej zawartość Schowka do obrazu  
  
1.  Z **Edytuj** menu, wybierz **Wklej**.  
  
     Zawartość Schowka otoczone obramowaniem wyboru pojawiają się w lewym górnym rogu okienka.  
  
2.  Umieść kursor w obrębie zaznaczenia i przeciągnij obrazu do odpowiedniej lokalizacji na obrazie.  
  
3.  Aby móc zakotwiczyć obrazu w nowej lokalizacji, kliknij przycisk poza zaznaczenia.  
  
### <a name="to-delete-the-current-selection-without-moving-it-to-the-clipboard"></a>Aby usunąć bieżące zaznaczenie bez przenoszenia go do Schowka  
  
1.  Z **Edytuj** menu, wybierz **usunąć**.  
  
     Pierwotnym obszarze zaznaczenie jest wypełniony bieżący kolor tła.  
  
    > [!NOTE]
    >  Dostęp do wycinania, kopiowania, wklejania i usunąć poleceń, klikając prawym przyciskiem myszy okno Widok zasobów.  
  
### <a name="to-move-the-selection"></a>Aby przenieść zaznaczone  
  
1.  Umieść wskaźnik wewnątrz obramowanie wyboru lub w dowolnym miejscu na nim, oprócz uchwytów zmiany rozmiaru.  
  
2.  Przeciągnij zaznaczenie do nowej lokalizacji.  
  
3.  Aby móc zakotwiczyć zaznaczenia w obrazie w nowej lokalizacji, kliknij poza zaznaczenia.  
  
 Aby uzyskać więcej informacji na rysunku zaznaczeniem, zobacz [Tworzenie pędzla niestandardowego](../windows/creating-a-custom-brush-image-editor-for-icons.md).  
  
 Aby uzyskać informacje o dodawaniu zasobów do projektów zarządzanych, zobacz [zasobów w aplikacjach pulpitu](https://msdn.microsoft.com/library/f45fce5x.aspx) w *Przewodnik programistów platformy .NET Framework.* Aby uzyskać informacje na ręczne dodanie do projektów zarządzanych plików zasobów, uzyskiwanie dostępu do zasobów, wyświetlanie zasoby statyczne i przypisanie do właściwości ciągów zasobów, zobacz [tworzenie plików zasobów dla aplikacji pulpitu](https://msdn.microsoft.com/library/xbx3z216.aspx). Informacje dotyczące globalizacji i lokalizacji zasobów w zarządzanych aplikacjach, zobacz [Globalizing i lokalizacja aplikacji .NET Framework](https://msdn.microsoft.com/library/h6270d0z.aspx).  
  
 Wymagania  
  
 Brak  
  
## <a name="see-also"></a>Zobacz też  
 [Klawisze skrótów](../windows/accelerator-keys-image-editor-for-icons.md)   
 [Edytowanie zasobów graficznych](../windows/editing-graphical-resources-image-editor-for-icons.md)   
 [Edytor obrazów dla ikon](../windows/image-editor-for-icons.md)

