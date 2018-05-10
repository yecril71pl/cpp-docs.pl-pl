---
title: Tworzenie nowej niestandardowej lub zasobów danych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.binary
dev_langs:
- C++
helpviewer_keywords:
- custom resources [C++]
- data resources [C++]
- resources [Visual Studio], creating
ms.assetid: 9918bf96-38fa-43a1-a384-572f95d84950
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c82e41544bde9cdd945e23f4ea5884e4e76ae22b
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
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
  
 Aby uzyskać informacje o dodawaniu zasobów do projektów zarządzanych, zobacz [zasobów w aplikacjach pulpitu](/dotnet/framework/resources/index) w *Przewodnik programistów platformy .NET Framework.* Aby uzyskać informacje na ręczne dodanie do projektów zarządzanych plików zasobów, uzyskiwanie dostępu do zasobów, wyświetlanie zasoby statyczne i przypisanie do właściwości ciągów zasobów, zobacz [tworzenie plików zasobów dla aplikacji pulpitu](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informacje dotyczące globalizacji i lokalizacji zasobów w zarządzanych aplikacjach, zobacz [Globalizing i lokalizacja aplikacji .NET Framework](/dotnet/standard/globalization-localization/index).  
  
 Wymagania  
  
 Win32  
  
## <a name="see-also"></a>Zobacz też  
 [Edytor plików binarnych](binary-editor.md)

