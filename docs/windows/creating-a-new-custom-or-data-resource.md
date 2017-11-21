---
title: "Tworzenie nowej niestandardowej lub zasobów danych | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.editors.binary
dev_langs: C++
helpviewer_keywords:
- custom resources [C++]
- data resources [C++]
- resources [Visual Studio], creating
ms.assetid: 9918bf96-38fa-43a1-a384-572f95d84950
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: ff1beb01e08ea78f96b7f161e7f3ffc1110ff63b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="creating-a-new-custom-or-data-resource"></a>Tworzenie nowej niestandardowej lub zasobów danych
Można utworzyć nowy zasób niestandardowy lub dane przez umieszczenie w osobnym pliku przy użyciu składni pliku skryptu (.rc) zasób normalny, a następnie łącznie z tym plikiem zasób prawym przyciskiem myszy projekt w Eksploratorze rozwiązań i klikając przycisk **zawiera zasobów**  menu skrótów.  
  
### <a name="to-create-a-new-custom-or-data-resource"></a>Aby utworzyć nowy zasób niestandardowy lub danych  
  
1. [Utwórz plik .rc](../windows/how-to-create-a-resource-script-file.md) zawiera zasób niestandardowy lub danych.  
  
     Niestandardowe dane można wpisać w plik .rc jako ciągi ujętego w cudzysłów zerem lub liczbami całkowitymi format dziesiętny, szesnastkową lub ósemkowe.  
  
2.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy plik .rc projektu, a następnie kliknij przycisk **zasobów zawiera** menu skrótów.  
  
3.  W **dyrektywy kompilacji** wpisz **#include** instrukcji, która nadaje nazwę pliku zawierającego niestandardowego zasobu. Na przykład:  
  
 ```  
    #include mydata.rc  
 ```  
  
     Upewnij się, że składnia i pisownię możesz wpisać są poprawne. Zawartość **dyrektywy kompilacji** pola są wstawiane do pliku skryptu zasobu, dokładnie tak, jak został wpisany.  
  
4.  Kliknij przycisk **OK** Aby zapisać zmiany.  
  
 Innym sposobem tworzenia niestandardowych zasobów jest zaimportować plik jako zasób niestandardowy. Aby uzyskać więcej informacji, zobacz [importowanie i eksportowanie zasobów](../windows/how-to-import-and-export-resources.md).  
  
 Aby uzyskać informacje o dodawaniu zasobów do projektów zarządzanych, zobacz [zasobów w aplikacjach pulpitu](https://msdn.microsoft.com/library/f45fce5x.aspx) w *Przewodnik programistów platformy .NET Framework.* Aby uzyskać informacje na ręczne dodanie do projektów zarządzanych plików zasobów, uzyskiwanie dostępu do zasobów, wyświetlanie zasoby statyczne i przypisanie do właściwości ciągów zasobów, zobacz [tworzenie plików zasobów dla aplikacji pulpitu](https://msdn.microsoft.com/library/xbx3z216.aspx). Informacje dotyczące globalizacji i lokalizacji zasobów w zarządzanych aplikacjach, zobacz [Globalizing i lokalizacja aplikacji .NET Framework](https://msdn.microsoft.com/library/h6270d0z.aspx).  
  
 Wymagania  
  
 Win32  
  
## <a name="see-also"></a>Zobacz też  
 [Edytor plików binarnych](binary-editor.md)

