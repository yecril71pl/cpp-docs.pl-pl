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
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0eca56e607c916e28afc7bf513d853bcf6d94b81
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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
  
 Aby uzyskać informacje o dodawaniu zasobów do projektów zarządzanych, zobacz [zasobów w aplikacjach pulpitu](/dotnet/framework/resources/index) w *Przewodnik programistów platformy .NET Framework.* Aby uzyskać informacje na ręczne dodanie do projektów zarządzanych plików zasobów, uzyskiwanie dostępu do zasobów, wyświetlanie zasoby statyczne i przypisanie do właściwości ciągów zasobów, zobacz [tworzenie plików zasobów dla aplikacji pulpitu](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informacje dotyczące globalizacji i lokalizacji zasobów w zarządzanych aplikacjach, zobacz [Globalizing i lokalizacja aplikacji .NET Framework](/dotnet/standard/globalization-localization/index).  
  
 **Wymagania**  
  
 Win32  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: otwieranie pliku skryptu zasobu spoza projektu (autonomiczna)](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)   
 [Edytory zasobów](../windows/resource-editors.md)

