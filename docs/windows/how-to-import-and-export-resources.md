---
title: 'Porady: importowanie i eksportowanie zasobów (C++) | Dokumentacja firmy Microsoft'
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
- resources [C++], exporting
- graphics [C++], exporting
- graphics [C++], importing
- resources [C++], importing
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
ms.openlocfilehash: a6b975b932545d62b62db0b44bad549a3570a602
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44318554"
---
# <a name="how-to-import-and-export-resources"></a>Porady: importowanie i eksportowanie zasobów

Możesz zaimportować zasobów graficznych (map bitowych, ikon, kursorów i pasków narzędzi), pliki HTML i zasobów niestandardowych do użytku w programie Visual C++. Możesz wyeksportować te same typy plików z projektu języka Visual C++ w oddzielnych plikach, które mogą być używane poza środowiskiem programowania.

> [!NOTE]
> Typy zasobów, takich jak akceleratorów, okna dialogowe i tabele ciągów nie można zaimportować lub wyeksportować, ponieważ nie są one typy plików autonomicznych.

### <a name="to-import-an-individual-resource-into-your-current-resource-file"></a>Aby zaimportować pojedynczy zasób do Twojego bieżącego pliku zasobu

1. W [widok zasobów](../windows/resource-view-window.md), kliknij prawym przyciskiem myszy węzeł skrypt zasobu (* .rc) plik, do którego chcesz dodać do zasobu.

2. Kliknij przycisk **importu** w menu skrótów.

3. Znajdź i wybierz nazwę pliku, mapa bitowa (bmp), ikona (.ico), kursora (.cur), plik Html (.htm) lub innego pliku, który chcesz zaimportować.

4. Kliknij przycisk **OK** można dodać zasobu do wybranego pliku w **zasobów** widoku.

   > [!NOTE]
   > Wybrane działa proces importowania, typ ten sam sposób niezależnie od tego, które określonego zasobu. Zaimportowane zasobów jest automatycznie dodawany do węzła poprawne dla tego typu zasobu.

### <a name="to-export-a-bitmap-icon-or-cursor-as-a-separate-file-for-use-outside-of-visual-c"></a>Aby wyeksportować mapy bitowej, ikona lub kursor postaci oddzielnych plików (do użytku poza programem Visual C++)

1. W **zasobów** wyświetlić, kliknij prawym przyciskiem myszy zasób, którą chcesz wyeksportować.

2. Kliknij przycisk **wyeksportować** w menu skrótów.

3. W **Eksportuj zasób** okna dialogowego pole, zaakceptuj nazwę bieżącego pliku lub wpisać nową.

4. Przejdź do folderu, w którym chcesz zapisać plik, a następnie kliknij przycisk **wyeksportować**.

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz też

[Pliki zasobów](../windows/resource-files-visual-studio.md)  
[Edytory zasobów](../windows/resource-editors.md)