---
title: "Wyświetlanie podglądu zasobów | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.resvw.resource.previewing
- vs.resvw.resource.previewing
dev_langs: C++
helpviewer_keywords:
- resources [Visual Studio], viewing
- resource previews
- code, viewing
ms.assetid: d6abda66-0e2b-4ac3-a59a-a57b8c6fb70b
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: bce36839b0736eabdbc850d9a2b2f9434cc820d1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="previewing-resources"></a>Wyświetlanie podglądu zasobów
Wyświetlanie podglądu zasobów służy do wyświetlania zasobów graficznych bez ich otwierania. Podgląd jest również przydatne dla plików wykonywalnych, po ich skompilowany, ponieważ zmiany numery identyfikatorów zasobów. Ponieważ te identyfikatory numeryczne często nie zawiera informacji wystarczających, wyświetlanie podglądu zasobów pomaga szybko zidentyfikować je.  
  
 Można wyświetlić podgląd układu wizualnego z następujących zasobów:  
  
-   Mapy bitowej  
  
-   Okno dialogowe  
  
-   Ikona  
  
-   Menu  
  
-   Kursor  
  
-   Pasek narzędzi  
  
 Funkcja wyświetlania podglądu nie ma zastosowania do zasobów akceleratora, Manifest tabeli ciągów i informacje o wersji.  
  
### <a name="to-preview-resources"></a>Aby wyświetlić podgląd zasobów  
  
1.  W [widok zasobów](../windows/resource-view-window.md) lub okno dokumentu, wybierz zasób, na przykład IDD_ABOUTBOX.  
  
     **Uwaga** Jeśli projekt nie zawiera już plik .rc, zobacz [Tworzenie nowego pliku skryptu zasobu](../windows/how-to-create-a-resource-script-file.md).  
  
2.  W [okna właściwości](/visualstudio/ide/reference/properties-window), kliknij przycisk **strony właściwości** przycisku.  
  
     \-lub -  
  
3.  Na **widoku** menu, kliknij przycisk **strony właściwości**.  
  
     Zostanie otwarta strona właściwości zasobu, wyświetlanie podglądu tego zasobu. Można następnie górę i w dół klawisze strzałek, aby przejść do drzewa w widoku zasobów lub okna dokumentu. Strona właściwości pozostanie otwarte i Pokaż dowolnego zasobu, który ma fokus i jest w stanie można wyświetlić podglądu.  
  
 Aby uzyskać informacje o dodawaniu zasobów do projektów zarządzanych, zobacz [zasobów w aplikacjach pulpitu](https://msdn.microsoft.com/library/f45fce5x.aspx) w *Przewodnik programistów platformy .NET Framework.* Aby uzyskać informacje na ręczne dodanie do projektów zarządzanych plików zasobów, uzyskiwanie dostępu do zasobów, wyświetlanie zasoby statyczne i przypisanie do właściwości ciągów zasobów, zobacz [tworzenie plików zasobów dla aplikacji pulpitu](https://msdn.microsoft.com/library/xbx3z216.aspx). Informacje dotyczące globalizacji i lokalizacji zasobów w zarządzanych aplikacjach, zobacz [Globalizing i lokalizacja aplikacji .NET Framework](https://msdn.microsoft.com/library/h6270d0z.aspx).  
  
 **Wymagania**  
  
 Win32  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: otwieranie pliku skryptu zasobu spoza projektu (autonomiczna)](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)   
 [Edytory zasobów](../windows/resource-editors.md)

