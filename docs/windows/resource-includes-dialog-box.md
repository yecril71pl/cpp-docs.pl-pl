---
title: Zasób zawiera okno dialogowe | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.resourceincludes
dev_langs:
- C++
helpviewer_keywords:
- Resource Includes dialog box
- rc files, changing storage
- symbol header files, changing
- compiling source code, including resources
- .rc files, changing storage
- symbol header files, read-only
- symbols, symbol header files
ms.assetid: 659a54e6-e416-4045-8411-798730ff4ce3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 756289bb819809fed63dba579c4ad1cd1e975780
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33879675"
---
# <a name="resource-includes-dialog-box"></a>Zasób zawiera okno dialogowe
Można użyć **zasobów zawiera** okno dialogowe, aby zmodyfikować rozmieszczenie normalnej pracy w środowisku przechowywania wszystkich zasobów w plik .rc projektu i wszystkie [symbole](../windows/symbols-resource-identifiers.md) w Resource.h.  
  
 Aby otworzyć **zasobów zawiera** okno dialogowe, kliknij prawym przyciskiem myszy .rc plików w [widok zasobów](../windows/resource-view-window.md), a następnie wybierz **zasobów zawiera** z menu skrótów.  
  
 **Plik nagłówka symbolu**  
 Umożliwia zmianę nazwy pliku nagłówka, gdzie są przechowywane definicje symbolu dla Twojego pliku zasobu. Aby uzyskać więcej informacji, zobacz [zmiana nazwy pliki nagłówka symboli](../windows/changing-the-names-of-symbol-header-files.md).  
  
 **Dyrektywy symboli tylko do odczytu**  
 Umożliwia dołączenie pliki nagłówkowe, które zawierają symbole, które nie powinien być modyfikowany podczas sesji. Na przykład można dołączyć plik symboli użytkowany przez kilku projektów. Mogą również obejmować pliki .h MFC. Aby uzyskać więcej informacji, zobacz [tym udostępnionych (tylko do odczytu) lub symbole obliczane](../windows/including-shared-read-only-or-calculated-symbols.md).  
  
 **Dyrektywy kompilacji**  
 Umożliwia dołączyć pliki zasobów, które zostały utworzone i edytowane oddzielnie od zasobów w pliku głównym zasobów zawierać dyrektyw kompilacji (na przykład takie, które zawierają warunkowo zasobów) lub zasobów w niestandardowym formacie. Aby dołączyć pliki zasobów MFC standardowe umożliwia także pole dyrektywy kompilacji. Aby uzyskać więcej informacji, zobacz [tym zasobów w czasie kompilowania](../windows/how-to-include-resources-at-compile-time.md).  
  
> [!NOTE]
>  Wyświetlane są pozycje w tych polach tekstowych w plik .rc oznaczony przez `TEXTINCLUDE 1`, `TEXTINCLUDE 2`, i `TEXTINCLUDE 3` odpowiednio. Aby uzyskać więcej informacji, zobacz [TN035: Korzystanie z wielu plików zasobów i plików nagłówków z programem Visual C++](../mfc/tn035-using-multiple-resource-files-and-header-files-with-visual-cpp.md).  
  
 Po dokonaniu zmiany używa pliku zasobu **zasobów zawiera** okno dialogowe, musisz zamknąć plik .rc i ponownie je, aby zmiany zaczęły obowiązywać. Aby uzyskać więcej informacji, zobacz [tym zasobów w czasie kompilowania](../windows/how-to-include-resources-at-compile-time.md).  
  

  
## <a name="requirements"></a>Wymagania  
 Win32  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: określanie katalogów dołączenia dla zasobów](../windows/how-to-specify-include-directories-for-resources.md)   
 [Symbole: Identyfikatory zasobów](../windows/symbols-resource-identifiers.md)   
 [Pliki zasobów](../windows/resource-files-visual-studio.md)   
 [Edytory zasobów](../windows/resource-editors.md)