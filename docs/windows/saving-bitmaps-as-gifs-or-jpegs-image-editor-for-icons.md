---
title: "Zapisywanie map bitowych jako plików GIF lub JPEG (edytor obrazów dla ikon) | Dokumentacja firmy Microsoft"
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
- .gif files, saving bitmaps as
- jpg files, saving bitmaps as
- jpeg files, saving bitmaps as
- .jpg files, saving bitmaps as
- Image editor [C++], converting image formats
- gif files, saving bitmaps as
- bitmaps [C++], converting formats
- .jpeg files, saving bitmaps as
- graphics [C++], converting formats
- images [C++], converting formats
ms.assetid: 115df69f-10fb-4e6f-906b-853c1e4a54af
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: f6bded97e27101981c17dce51d7fc9ecb9cd8d55
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="saving-bitmaps-as-gifs-or-jpegs-image-editor-for-icons"></a>Zapisywanie map bitowych jako plików GIF lub JPEG (Edytor obrazów dla ikon)
Podczas tworzenia mapy bitowej obraz jest tworzony w formacie Mapa bitowa (bmp). Można jednak zapisać obrazu GIF lub JPEG lub w innych formatach graficznych.  
  
> [!NOTE]
>  Ten proces nie ma zastosowania do ikony i kursory.  
  
### <a name="to-create-and-save-a-bitmap-as-a-gif-or-jpeg"></a>Aby utworzyć i zapisać map bitowych jako GIF lub JPEG  
  
1.  Z **pliku** menu, wybierz **Otwórz**, następnie kliknij przycisk **pliku**.  
  
2.  W **okno dialogowe Nowy plik**, kliknij przycisk **Visual C++** folderu, następnie wybierz **pliku mapa bitowa (bmp)** w **szablony** polu i kliknij przycisk  **Otwórz**.  
  
     Otwiera mapy bitowej w **obrazu** edytora.  
  
3.  Wprowadzanie zmian do nowej mapy bitowej zgodnie z potrzebami.  
  
4.  Mapą bitową wciąż otwarty w **obrazu** edytorze kliknij **zapisać *filename*.bmp jako** na **pliku** menu.  
  
5.  W **Zapisz plik jako** oknie dialogowym wpisz nazwę chcesz nadać plików i rozszerzenia plików, które określa format pliku w **nazwę pliku** pole. Na przykład myfile.gif.  
  
     **Uwaga** należy utworzyć lub otworzyć mapy bitowej poza projektu, aby zapisać go jako innego formatu pliku. Utwórz lub otwórz go w projekcie, **Zapisz jako** polecenie jest niedostępne. Aby uzyskać więcej informacji, zobacz [wyświetlania zasobów w zasobu skryptu pliku poza of projektu (autonomicznego)](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md).  
  
6.  Kliknij przycisk **zapisać**.  
  
 Aby uzyskać informacje o dodawaniu zasobów do projektów zarządzanych, zobacz [zasobów w aplikacjach pulpitu](https://msdn.microsoft.com/library/f45fce5x.aspx) w *Przewodnik programistów platformy .NET Framework.* Aby uzyskać informacje na ręczne dodanie do projektów zarządzanych plików zasobów, uzyskiwanie dostępu do zasobów, wyświetlanie zasoby statyczne i przypisanie do właściwości ciągów zasobów, zobacz [tworzenie plików zasobów dla aplikacji pulpitu](https://msdn.microsoft.com/library/xbx3z216.aspx). Informacje dotyczące globalizacji i lokalizacji zasobów w zarządzanych aplikacjach, zobacz [Globalizing i lokalizacja aplikacji .NET Framework](https://msdn.microsoft.com/library/h6270d0z.aspx).  
  
## <a name="see-also"></a>Zobacz też  
 [Edytowanie zasobów graficznych](../windows/editing-graphical-resources-image-editor-for-icons.md)   
 [Edytor obrazów dla ikon](../windows/image-editor-for-icons.md)

