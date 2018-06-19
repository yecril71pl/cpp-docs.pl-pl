---
title: Wyrównywanie kontrolek do prowadnicy | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a7c8cc57b4d2e7150ff09858cfd5b315beb37962
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33857841"
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
  
 Aby uzyskać informacje o dodawaniu zasobów do projektów zarządzanych, zobacz [zasobów w aplikacjach pulpitu](/dotnet/framework/resources/index) w *Przewodnik programistów platformy .NET Framework.* Aby uzyskać informacje na ręczne dodanie do projektów zarządzanych plików zasobów, uzyskiwanie dostępu do zasobów, wyświetlanie zasoby statyczne i przypisanie do właściwości ciągów zasobów, zobacz [tworzenie plików zasobów dla aplikacji pulpitu](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informacje dotyczące globalizacji i lokalizacji zasobów w zarządzanych aplikacjach, zobacz [Globalizing i lokalizacja aplikacji .NET Framework](/dotnet/standard/globalization-localization/index).  
  
 Wymagania  
  
 Win32  
  
## <a name="see-also"></a>Zobacz też  
 [Stany Edytor okien dialogowych (prowadnice i siatki)](../windows/dialog-editor-states-guides-and-grids.md)   
 [Kontrolki w oknach dialogowych](../windows/controls-in-dialog-boxes.md)

