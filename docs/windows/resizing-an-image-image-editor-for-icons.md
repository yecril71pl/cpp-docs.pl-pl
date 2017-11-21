---
title: "Zmiana rozmiaru obrazu (edytor obrazów dla ikon) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.editors.image.editing
dev_langs: C++
helpviewer_keywords:
- Image editor [C++], resizing images
- graphics [C++], resizing
- images [C++], resizing
- resizing images
ms.assetid: d83a02c4-4dfe-4586-a0df-51a50c2ba71d
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 6c6e8d5e4704f9dda9399d67de5b3d0f93d283a7
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="resizing-an-image-image-editor-for-icons"></a>Zmiana rozmiaru obrazu (Edytor obrazów dla ikon)
Zachowanie edytor obrazów podczas zmiany rozmiaru obrazu zależy od tego, czy znasz [wybranego](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md) całego obrazu lub jego część.  
  
 Zaznaczenie zawiera tylko część obrazu, edytor obrazów zmniejsza zaznaczenie przez usunięcie wierszy lub kolumn pikseli i wypełnianie vacated regionów bieżący kolor tła lub rozciąga się zaznaczenie zduplikowane wiersze lub kolumny w pikselach.  
  
 Jeśli zaznaczenie obejmuje całego obrazu, edytor obrazów albo zmniejsza rozciąga się obraz lub przycina i rozszerza on.  
  
 Istnieją dwa mechanizmy do zmiany rozmiaru obrazu: uchwytów zmiany rozmiaru i [okna właściwości](/visualstudio/ide/reference/properties-window). Możesz przeciągnąć uchwyty zmiany rozmiaru, aby zmienić rozmiar wszystkich lub część obrazu. Uchwyty zmiany rozmiaru, które możesz przeciągnąć są wypełnione. Nie można przeciągnąć dojść, które są puste. Można użyć właściwości okno, aby zmienić rozmiar całego obrazu, wybranej części.  
  
 ![Uchwytów na mapę bitową](../mfc/media/vcimageeditorsizinghandles.gif "vcImageEditorSizingHandles")  
Uchwyty zmiany rozmiaru  
  
> [!NOTE]
>  Jeśli masz opcji siatki kafelka w [okno dialogowe Ustawienia siatki](../windows/grid-settings-dialog-box-image-editor-for-icons.md), zmiana rozmiaru przyciąganie do następnego wiersza siatki kafelka. Siatka pikseli, opcja jest zaznaczona (ustawienie domyślne), jeśli tylko zmiany rozmiaru przyciąganie do następnego pikseli dostępne.  
  
-   [Zmiana rozmiaru całego obrazu](../windows/resizing-an-entire-image-image-editor-for-icons.md)  
  
-   [Przycinanie i rozszerzanie całego obrazu](cropping-or-extending-an-entire-image-image-editor-for-icons.md)  
  
-   [Zmniejszanie i rozciąganie całego obrazu](../windows/shrinking-or-stretching-an-entire-image-image-editor-for-icons.md)  
  
-   [Zmniejszanie i rozciąganie części obrazu](../windows/shrinking-or-stretching-part-of-an-image-image-editor-for-icons.md)  
  
 Aby uzyskać informacje o dodawaniu zasobów do projektów zarządzanych, zobacz [zasobów w aplikacjach pulpitu](https://msdn.microsoft.com/library/f45fce5x.aspx) w *Przewodnik programistów platformy .NET Framework.* Aby uzyskać informacje na ręczne dodanie do projektów zarządzanych plików zasobów, uzyskiwanie dostępu do zasobów, wyświetlanie zasoby statyczne i przypisanie do właściwości ciągów zasobów, zobacz [tworzenie plików zasobów dla aplikacji pulpitu](https://msdn.microsoft.com/library/xbx3z216.aspx). Informacje dotyczące globalizacji i lokalizacji zasobów w zarządzanych aplikacjach, zobacz [Globalizing i lokalizacja aplikacji .NET Framework](https://msdn.microsoft.com/library/h6270d0z.aspx).  
  
## <a name="requirements"></a>Wymagania  
 Brak  
  
## <a name="see-also"></a>Zobacz też  
 [Klawisze skrótów](../windows/accelerator-keys-image-editor-for-icons.md)   
 [Edytowanie zasobów graficznych](../windows/editing-graphical-resources-image-editor-for-icons.md)   
 [Edytor obrazów dla ikon](../windows/image-editor-for-icons.md)

