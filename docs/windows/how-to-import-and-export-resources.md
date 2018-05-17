---
title: 'Porady: importowanie i eksportowanie zasobów | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vs.resvw.resource.importing
- vc.resvw.resource.importing
dev_langs:
- C++
helpviewer_keywords:
- resources [Visual Studio], exporting
- graphics [C++], exporting
- graphics [C++], importing
- resources [Visual Studio], importing
- bitmaps [C++], importing and exporting
- toolbars [C++], importing
- images [C++], importing
- toolbars [C++], exporting
- cursors [C++], importing and exporting
- images [C++], exporting
ms.assetid: 3c9329dc-dcb8-4edd-a600-78e3e572bd89
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9e526ab335436730f4132b5b7127ec9079432a4a
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
---
# <a name="how-to-import-and-export-resources"></a>Porady: importowanie i eksportowanie zasobów
Możesz zaimportować zasobów graficznych (mapy bitowe, ikony kursory i paski narzędzi), plików HTML i zasobów niestandardowych do użytku w programie Visual C++. Możesz wyeksportować takich samych typach plików z projektu programu Visual C++ w oddzielnych plikach, które mogą być używane poza Środowisko deweloperskie.  
  
> [!NOTE]
>  Typy zasobów, takich jak akceleratorów, okna dialogowe i tabele ciągów nie może zaimportować lub wyeksportować, ponieważ nie są one typów plików autonomicznych.  
  
### <a name="to-import-an-individual-resource-into-your-current-resource-file"></a>Aby zaimportować pojedynczego zasobu do bieżącego pliku zasobów  
  
1.  W [widok zasobów](../windows/resource-view-window.md), kliknij prawym przyciskiem myszy węzeł skrypt zasobu (* .rc) pliku, do której chcesz dodać zasobu.  
  
2.  Kliknij przycisk **importu** menu skrótów.  
  
3.  Znajdź i wybierz nazwę pliku, mapa bitowa (bmp), ikona (.ico), kursora (.cur), plik Html (.htm) lub innego pliku, który chcesz zaimportować.  
  
4.  Kliknij przycisk **OK** można dodać zasobu do wybranego pliku w **zasobów** widoku.  
  
    > [!NOTE]
    >  Wybrano działa proces importu, tak samo, niezależnie od tego, którego zasobu określonego typu. Importowanych zasobów jest automatycznie dodawany do węzła poprawne dla tego typu zasobu.  
  
### <a name="to-export-a-bitmap-icon-or-cursor-as-a-separate-file-for-use-outside-of-visual-c"></a>Aby wyeksportować mapy bitowej, ikona lub kursora w oddzielnym pliku (na potrzeby używania poza Visual C++)  
  
1.  W **zasobów** wyświetlić, kliknij prawym przyciskiem myszy zasobów do wyeksportowania.  
  
2.  Kliknij przycisk **wyeksportować** menu skrótów.  
  
3.  W **eksportu zasobu** okna dialogowego Zaakceptuj bieżącej nazwy pliku lub wpisz nową.  
  
4.  Przejdź do folderu, w którym chcesz zapisać plik, a następnie kliknij przycisk **wyeksportować**.  
  

  
 Wymagania  
  
 Win32  
  
## <a name="see-also"></a>Zobacz też  
 [Pliki zasobów](../windows/resource-files-visual-studio.md)   
 [Edytory zasobów](../windows/resource-editors.md)