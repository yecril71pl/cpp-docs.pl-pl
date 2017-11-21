---
title: "Wybieranie tła przezroczystego lub nieprzezroczystego (edytor obrazów dla ikon) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- opaque backgrounds
- background colors, images
- colors [C++], image
- Image editor [C++], transparent or opague backgrounds
- background images
- images [C++], transparency
- images [C++], opaque background
- transparent backgrounds
- transparency, background
- transparent backgrounds, images
ms.assetid: 61b743d9-c86b-405d-9a81-0806431b4363
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: ea4c5ae14bdf11583a3aba21dfd90e0a6f2fd92a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="choosing-a-transparent-or-opaque-background-image-editor-for-icons"></a>Wybieranie tła przezroczystego lub nieprzezroczystego (Edytor obrazów dla ikon)
Podczas przenoszenia lub skopiowane z obrazu pikseli w zaznaczeniu, które odpowiadają bieżący kolor tła są domyślnie przezroczyste; nie ograniczają pikseli w lokalizacji docelowej.  
  
 Można przełączyć na tło nieprzezroczyste przezroczyste tło (ustawienie domyślne) i z powrotem. Podczas używania narzędzia wyboru **przezroczyste tło** i **tło nieprzezroczyste** dostępne są opcje w selektorze opcja **edytor obrazów** paska narzędzi (jak pokazano poniżej).  
  
 ![Opcje tła &#45; przezroczystości](../windows/media/vcimageeditoropaqtranspback.gif "vcImageEditorOpaqTranspBack")  
Przezroczyste i nieprzezroczyste opcji paska narzędzi edytora obrazów  
  
### <a name="to-switch-between-a-transparent-and-opaque-background"></a>Aby przełączyć między tło przezroczyste i nieprzezroczyste  
  
1.  W **edytor obrazów** narzędzi, kliknij przycisk **opcji** selektora, a następnie kliknij odpowiednią tła:  
  
    -   **Tło nieprzezroczyste (IE)**: istniejącego obrazu jest zasłonięty przez wszystkie części zaznaczenia.  
  
    -   **Przezroczyste tło T**: istniejący obraz pokazuje za pośrednictwem części zaznaczenie zgodne bieżący kolor tła.  
  
 \-lub -  
  
-   Na **obrazu** menu, wybierz lub wyczyść pole wyboru **Rysowanie nieprzezroczystych**.  
  
 Można zmienić kolor tła, gdy poprzedni wybór jest już w obiekcie do zmiany, które części obrazu są niewidoczne.  
  
 Aby uzyskać informacje o dodawaniu zasobów do projektów zarządzanych, zobacz [zasobów w aplikacjach pulpitu](https://msdn.microsoft.com/library/f45fce5x.aspx) w *Przewodnik programistów platformy .NET Framework.* Aby uzyskać informacje na ręczne dodanie do projektów zarządzanych plików zasobów, uzyskiwanie dostępu do zasobów, wyświetlanie zasoby statyczne i przypisanie do właściwości ciągów zasobów, zobacz [tworzenie plików zasobów dla aplikacji pulpitu](https://msdn.microsoft.com/library/xbx3z216.aspx). Informacje dotyczące globalizacji i lokalizacji zasobów w zarządzanych aplikacjach, zobacz [Globalizing i lokalizacja aplikacji .NET Framework](https://msdn.microsoft.com/library/h6270d0z.aspx).  
  
 Wymagania  
  
 Brak  
  
## <a name="see-also"></a>Zobacz też  
 [Klawisze skrótów](../windows/accelerator-keys-image-editor-for-icons.md)   
 [Praca z kolorem](../windows/working-with-color-image-editor-for-icons.md)