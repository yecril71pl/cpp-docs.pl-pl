---
title: Testowanie okna dialogowego | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Test Dialog command
- testing, dialog boxes
- dialog boxes, testing
ms.assetid: 45034ee9-c554-4f4b-8c46-6ddefdee8951
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 307b5ffeeaa21b4cb90779a9d516229bf2ab3167
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2018
ms.locfileid: "40019681"
---
# <a name="testing-a-dialog-box"></a>Testowanie okna dialogowego
Podczas projektowania okna dialogowego, można symulować i testować jej zachowania w czasie wykonywania bez kompilacji programu. W tym trybie możesz wykonywać następujące czynności:  
  
-   Wpisz tekst, wybierz z listy pola kombi, włączanie lub wyłączanie opcji i wybierz polecenia.  
  
-   Przetestuj kolejność tabulacji.  
  
-   Przetestuj zgrupowania formantów, takich jak pola wyboru i przyciski opcji.  
  
-   Przetestuj skróty klawiaturowe dla formantów w oknie dialogowym.  
  
    > [!NOTE]
    >  Połączenia do kodu pola dialogowego przy użyciu kreatorów nie są objęte symulacją.  
  
 Podczas testowania okna dialogowego, zwykle wyświetla się ono w lokalizacji, która jest określana względem okna głównego programu. Jeśli ustawiono okno dialogowe **bezwzględnie Wyrównaj** właściwości **True**, okno dialogowe jest wyświetlane w położeniu względem lewego górnego rogu ekranu.  
  
### <a name="to-test-a-dialog-box"></a>Aby przetestować okno dialogowe  
  
1.  Gdy **okna dialogowego** edytora jest aktywnym oknem, na pasku menu, wybierz polecenie **Format** > **Test dialogowy**.  
  
2.  Aby zakończyć symulację, naciśnij klawisz **Esc**, lub po prostu wybierz **Zamknij** przycisku w oknie dialogowym, które testujesz.  
  
 Aby uzyskać informacje dotyczące sposobu dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index).  
  
## <a name="requirements"></a>Wymagania  
 Win32  
  
## <a name="see-also"></a>Zobacz też  
 [Formanty w oknach dialogowych](../windows/controls-in-dialog-boxes.md)   
 [Edytor okien dialogowych](../windows/dialog-editor.md)   
 [Pokazywanie i ukrywanie paska narzędzi Edytora okien dialogowych](../windows/showing-or-hiding-the-dialog-editor-toolbar.md)