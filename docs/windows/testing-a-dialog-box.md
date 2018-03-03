---
title: Testowanie okna dialogowego | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- Test Dialog command
- testing, dialog boxes
- dialog boxes, testing
ms.assetid: 45034ee9-c554-4f4b-8c46-6ddefdee8951
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d81d288453e56acfb02a123075692b907d371578
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="testing-a-dialog-box"></a>Testowanie okna dialogowego
Podczas projektowania okno dialogowe, można symulować i przetestować jego zachowania w czasie wykonywania bez kompilowania programu. W tym trybie można wykonywać następujące czynności:  
  
-   Wpisz tekst, wybierz z listy pola kombi, włączanie lub wyłączanie opcji i wybrać polecenie.  
  
-   Przetestuj kolejności tabulacji.  
  
-   Przetestuj grupowanie formanty, takie jak przycisków radiowych i pól wyboru.  
  
-   Przetestuj skróty klawiaturowe dla formantów w oknie dialogowym.  
  
    > [!NOTE]
    >  Połączenia wysłane za pomocą kreatorów kodu pole okna dialogowego nie znajdują się w symulacji.  
  
 Podczas testowania okno dialogowe zwykle wyświetlane w lokalizacji, która jest względem okno główne programu. Jeśli okno dialogowe właściwości wyrównanie bezwzględne ustawiono wartość true, okno dialogowe wyświetla na pozycji, która jest względem lewego górnego rogu ekranu.  
  
### <a name="to-test-a-dialog-box"></a>Aby przetestować okno dialogowe  
  
1.  Gdy okno edytora jest aktywne okno na pasku menu wybierz pozycję **Format**, **okno dialogowe testu**.  
  
2.  Aby zakończyć symulacji, naciśnij klawisz Esc, lub po prostu wybierz **Zamknij** przycisk w oknie dialogowym podczas testowania.  
  
 Aby uzyskać informacje o tym, jak dodać zasoby do projektów zarządzanych, zobacz [zasobów w aplikacjach pulpitu](/dotnet/framework/resources/index).  
  
 Wymagania  
  
 Win32  
  
## <a name="see-also"></a>Zobacz też  
 [Formanty w oknach dialogowych](../windows/controls-in-dialog-boxes.md)   
 [Edytor okien dialogowych](../windows/dialog-editor.md)   
 [Pokazywanie i ukrywanie paska narzędzi Edytora okien dialogowych](../windows/showing-or-hiding-the-dialog-editor-toolbar.md)

