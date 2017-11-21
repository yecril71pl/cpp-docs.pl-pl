---
title: "Wyrównywanie kontrolek do prowadnicy | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- DLUs (dialog units)
- controls [C++], aligning
- Dialog editor, snap to guides
- guides, tick mark interval
- dialog box controls, placement
- guides, aligning controls
- dialog units (DLUs)
- snap to guides (Dialog editor)
- controls [C++], sizing
- tick mark interval in Dialog editor
- controls [C++], snap to guides/grid
ms.assetid: 17db84ba-5288-4478-be57-afa748aa6447
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 65eef3ef17e46e86a302b614b88413c97b045616
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="aligning-controls-on-a-guide"></a>Dopasowanie kontrolek do prowadnicy
Uchwyty zmiany rozmiaru formantów przyciąganie do prowadnic po przeniesieniu formantów i przewodniki przyciąganie do kontrolek (Jeśli nie istnieją żadne formanty przypięty wcześniej do przewodnika). Po przeniesieniu przewodnik także przenieść formantów, które mają być przyciągane do niego. Formanty przyciągnięte do więcej niż jeden podręcznik zmieniany jest rozmiar po jednym przewodniki jest przenoszony.  
  
 Znaczniki w linijki określające odstępów prowadnice i formanty są definiowane przez jednostki okna dialogowego (Dlu). DLU opiera się na rozmiar czcionki okno dialogowe, zwykle punktu 8 MS Shell Dlg. Poziomy DLU jest średniej szerokości czcionki okno dialogowe podzielona przez cztery. DLU pionowe jest średnią wysokość czcionki podzielić przez 8.  
  
### <a name="to-size-a-group-of-controls-with-guides"></a>Rozmiar grupy formantów z liniami  
  
1.  Przyciąganie jednej stronie formantu (lub formantów) do prowadnicy.  
  
2.  Przeciągnij Przewodnik po drugiej stronie formantu (lub formantów).  
  
     W razie potrzeby z wielu formantów rozmiar każdego przyciągane do prowadnicy drugiego.  
  
3.  Przenieś albo przewodnik do rozmiaru formantu (lub formantów).  
  
### <a name="to-change-the-intervals-of-the-tick-marks"></a>Aby zmienić interwałów znaczników  
  
1.  Z **Format** menu, wybierz **ustawień przewodnika**.  
  
2.  W [okno dialogowe Ustawienia prowadnic](../windows/guide-settings-dialog-box.md)w **odstępy między liniami siatki** określ nową szerokość i wysokość w Dlu.  
  
 Aby uzyskać informacje o dodawaniu zasobów do projektów zarządzanych, zobacz [zasobów w aplikacjach pulpitu](https://msdn.microsoft.com/library/f45fce5x.aspx) w *Przewodnik programistów platformy .NET Framework.* Aby uzyskać informacje na ręczne dodanie do projektów zarządzanych plików zasobów, uzyskiwanie dostępu do zasobów, wyświetlanie zasoby statyczne i przypisanie do właściwości ciągów zasobów, zobacz [tworzenie plików zasobów dla aplikacji pulpitu](https://msdn.microsoft.com/library/xbx3z216.aspx). Informacje dotyczące globalizacji i lokalizacji zasobów w zarządzanych aplikacjach, zobacz [Globalizing i lokalizacja aplikacji .NET Framework](https://msdn.microsoft.com/library/h6270d0z.aspx).  
  
 Wymagania  
  
 Win32  
  
## <a name="see-also"></a>Zobacz też  
 [Stany Edytor okien dialogowych (prowadnice i siatki)](../windows/dialog-editor-states-guides-and-grids.md)   
 [Formanty w oknach dialogowych](../windows/controls-in-dialog-boxes.md)

