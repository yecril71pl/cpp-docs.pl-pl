---
title: Przenoszenie ciągu z jednego pliku zasobu do innego | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- strings [C++], moving between files
- resource script files, moving strings
- string editing, moving strings between resources
- String editor, moving strings between files
ms.assetid: 94f8ee81-9b4c-4788-ba95-68c58db38029
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1481f04b88d6ab63486885d93b971c3023d3e0d2
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33879272"
---
# <a name="moving-a-string-from-one-resource-file-to-another"></a>Przenoszenie ciągu z jednego pliku zasobu do innego
### <a name="to-move-a-string-from-one-resource-script-file-to-another"></a>Aby przenieść plik skryptu jeden zasób ciągu  
  
1.  Otwórz tabele ciągów w obu .RC — pliki. (Aby uzyskać więcej informacji, zobacz [wyświetlania zasobów w zasobu skryptu pliku poza z projektem](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md).)  
  
    > [!NOTE]
    >  Jeśli projekt nie zawiera już plik .rc, zobacz [Tworzenie nowego pliku skryptu zasobu](../windows/how-to-create-a-resource-script-file.md).  
  
2.  Kliknij prawym przyciskiem myszy ciąg, który ma zostać przeniesiona, a następnie wybierz **Wytnij** z menu skrótów.  
  
3.  Umieść kursor w miejscu docelowym **edytor ciągów** okna.  
  
4.  W pliku .rc, do którego chcesz przenieść ciąg, kliknij prawym przyciskiem myszy i wybierz polecenie **Wklej** z menu skrótów.  
  
    > [!NOTE]
    >  Jeśli **identyfikator** lub **wartość** ciąg przeniesionego powoduje konflikt z istniejącym **identyfikator** lub **wartość** w pliku docelowym albo **Identyfikator** lub **wartość** zmian przeniesionego ciągu. Jeśli istnieje ciąg o takim samym **identyfikator**, **identyfikator** zmian przeniesionego ciągu. Jeśli istnieje ciąg o takim samym **wartość**, **wartość** zmian przeniesionego ciągu.  
  
 Aby uzyskać informacje o dodawaniu zasobów do projektów zarządzanych (te, których miejscem docelowym jest środowisko uruchomieniowe języka wspólnego), zobacz [zasobów w aplikacjach pulpitu](/dotnet/framework/resources/index) w *Przewodnik programistów platformy .NET Framework.* Aby uzyskać informacje na ręczne dodanie do projektów zarządzanych plików zasobów, uzyskiwanie dostępu do zasobów, wyświetlanie zasoby statyczne i przypisanie do właściwości ciągów zasobów, zobacz [wskazówki: Lokalizowanie formularzy systemu Windows](http://msdn.microsoft.com/en-us/9a96220d-a19b-4de0-9f48-01e5d82679e5) i [Wskazówki: Korzystanie z zasobów dla lokalizacji ASP.NET](http://msdn.microsoft.com/Library/bb4e5b44-e2b0-48ab-bbe9-609fb33900b6).  
  
 **Wymagania**  
  
 Win32  
  
## <a name="see-also"></a>Zobacz też  
 [Edytor ciągów](../windows/string-editor.md)   
 [Pliki zasobów](../windows/resource-files-visual-studio.md)   
 [Dostosowywanie układów okien](/visualstudio/ide/customizing-window-layouts-in-visual-studio)   

