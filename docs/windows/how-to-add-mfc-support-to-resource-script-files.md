---
title: 'Porady: Dodawanie obsługi MFC do plików skryptu zasobu | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.resvw.add.MFC
dev_langs:
- C++
helpviewer_keywords:
- rc files, adding MFC support
- .rc files, adding MFC support
- MFC, adding support to resource scripts files
- resource script files, adding MFC support
ms.assetid: 599dfe9d-ad26-4e34-899c-49b56599e37f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 659c974fccec0e54dc42d6d1a5bdb019747f81ff
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39647027"
---
# <a name="how-to-add-mfc-support-to-resource-script-files"></a>Porady: dodawanie obsługi MFC do plików skryptu zasobu
Zwykle podczas kompilowania aplikacji MFC dla Windows przy użyciu [Kreator aplikacji MFC](../mfc/reference/mfc-application-wizard.md), Kreator generuje zestaw podstawowych plików (w tym pliku zasobu skryptu (.rc)), który zawiera podstawowe funkcje programu Microsoft Foundation klasy (MFC). Jednak jeśli edytujesz plik .rc dla aplikacji Windows, która nie jest oparty na bibliotece MFC, następujące funkcje specyficzne dla platformy MFC nie są dostępne:  
  
-   Kreatorzy kodu MFC (wcześniej nazywane "[Kreator klas MFC](http://msdn.microsoft.com/98dc2434-ba93-4e0b-b084-1a4bc26cdf1e)")  
  
-   Ciągi menu podpowiedzi  
  
-   Zawartość list dla formantów pola kombi  
  
-   Obsługa formantu ActiveX  
  
 Można jednak dodać obsługę MFC do istniejących plików .rc, które nie mają.  
  
### <a name="to-add-mfc-support-to-rc-files"></a>Aby dodać obsługę MFC do plików .rc  
  
1.  Otwórz pliku skryptu zasobu.  
  
    > [!NOTE]
    >  Jeśli projekt nie zawiera jeszcze pliku .rc, zobacz [tworzenia nowego pliku skryptu zasobów](../windows/how-to-create-a-resource-script-file.md).  
  
2.  W [widok zasobów](../windows/resource-view-window.md), wyróżnij folder zasobów (na przykład MFC.rc).  
  
3.  W [okno właściwości](/visualstudio/ide/reference/properties-window)ustaw **tryb MFC** właściwości **True**.  
  
    > [!NOTE]
    >  Oprócz ustawienia tej flagi, plik .rc musi być częścią projektu MFC. Na przykład, ustawienie tylko **tryb MFC** do **True** w pliku .rc w systemie Win32 projektu nie daje żadnych funkcji MFC.  
  
## <a name="requirements"></a>Wymagania  
 MFC  
  
## <a name="see-also"></a>Zobacz też  
 [Pliki zasobów](../windows/resource-files-visual-studio.md)   
 [Edytory zasobów](../windows/resource-editors.md)