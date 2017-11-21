---
title: "Porady: Dodawanie obsługi MFC do plików skryptu zasobu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.resvw.add.MFC
dev_langs: C++
helpviewer_keywords:
- rc files, adding MFC support
- .rc files, adding MFC support
- MFC, adding support to resource scripts files
- resource script files, adding MFC support
ms.assetid: 599dfe9d-ad26-4e34-899c-49b56599e37f
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 1d931c1309d583b8904afa403130411e495e0408
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-add-mfc-support-to-resource-script-files"></a>Porady: dodawanie obsługi MFC do plików skryptu zasobu
Zwykle podczas budowania aplikacji MFC dla systemu Windows przy użyciu [Kreator aplikacji MFC](../mfc/reference/mfc-application-wizard.md), Kreator generuje podstawowego zestawu plików (w tym pliku skryptu (.rc) zasobu), który zawiera podstawowe funkcje programu Microsoft Foundation klasy (MFC). Jednak w przypadku edycji plik .rc dla aplikacji systemu Windows, który nie jest oparty na MFC, następujące funkcje specyficzne dla programu MFC framework nie są dostępne:  
  
-   Kreatorzy kodów MFC (wcześniej nazywane "[MFC ClassWizard](http://msdn.microsoft.com/en-us/98dc2434-ba93-4e0b-b084-1a4bc26cdf1e)")  
  
-   Ciągi monitu menu  
  
-   Wyświetlanie zawartości dla formantów pola kombi  
  
-   Hosting kontrolki ActiveX  
  
 Można jednak dodać obsługę MFC do istniejących .RC — pliki, które nie mają.  
  
### <a name="to-add-mfc-support-to-rc-files"></a>Aby dodać obsługę MFC do .RC — pliki  
  
1.  Otwórz pliku skryptu zasobu.  
  
    > [!NOTE]
    >  Jeśli projekt nie zawiera już plik .rc, zobacz [Tworzenie nowego pliku skryptu zasobu](../windows/how-to-create-a-resource-script-file.md).  
  
2.  W [widok zasobów](../windows/resource-view-window.md), zaznacz folder zasoby (na przykład MFC.rc).  
  
3.  W [okna właściwości](/visualstudio/ide/reference/properties-window)ustaw **tryb MFC** właściwości **True**.  
  
    > [!NOTE]
    >  Poza ustawieniem tej flagi, plik .rc musi być częścią projektu MFC. Na przykład tylko ustawienie **tryb MFC** do **True** na plik .rc w Win32 projektu nie zapewniają funkcji MFC.  
  

  
 **Wymagania**  
  
 MFC  
  
## <a name="see-also"></a>Zobacz też  
 [Pliki zasobów](../windows/resource-files-visual-studio.md)   
 [Edytory zasobów](../windows/resource-editors.md)