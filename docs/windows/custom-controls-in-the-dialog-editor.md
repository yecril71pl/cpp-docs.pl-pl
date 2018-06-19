---
title: Formanty niestandardowe w edytorze okien dialogowych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- Custom Control
dev_langs:
- C++
helpviewer_keywords:
- controls [C++], templates
- custom controls [Visual Studio], dialog boxes
- custom controls [Visual Studio]
- dialog box controls, custom (user) controls
- Dialog editor, custom controls
ms.assetid: f494b314-4000-4bbe-bbd0-4b18fb71ede1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2c2bca249958e4d25ab5377540525da34802ac04
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33880247"
---
# <a name="custom-controls-in-the-dialog-editor"></a>Formanty niestandardowe w Edytorze okien dialogowych
Edytor okien dialogowych umożliwia użycie istniejących "niestandardowe" lub "użytkownika" formantów w szablonie — okno dialogowe.  
  
> [!NOTE]
>  Niestandardowe formanty w tym sensie są nie należy mylić z formantami ActiveX. Formanty ActiveX były nazywane niestandardowych formantów OLE. Ponadto nie należy mylić tych kontrolek z formantami rysowanych przez właściciela w systemie Windows.  
  
 Ta funkcja ma na celu umożliwiają używanie formantów innych niż te dostarczone przez system Windows. W czasie wykonywania formantu jest skojarzony z klasy okna (nie taka sama jak klasa C++). Najpopularniejszym sposobem wykonania tego samego zadania jest zainstalować żadnego formantu, takich jak kontrola statycznych, w oknie dialogowym. Następnie w czasie wykonywania w [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog) funkcji, Usuń ten formant i Zamień własne kontrolki niestandardowej.  
  
 Jest to technika stary. Dzisiaj zalecana w większości przypadków zapisu formantu ActiveX lub podklasy formantu wspólnego systemu Windows.  
  
 W przypadku tych kontrolek niestandardowych jest ograniczona do:  
  
-   Ustawianie lokalizacji w oknie dialogowym.  
  
-   Wpisywanie podpis.  
  
-   Identyfikowanie nazwę klasy systemu Windows formantu (kod aplikacji należy zarejestrować formant o tej nazwie).  
  
-   Wpisywanie 32-bitową wartość szesnastkowa, która ustawia styl formantu.  
  
-   Ustawienie rozszerzonego stylu.  
  
 Aby uzyskać informacje o dodawaniu zasobów do projektów zarządzanych, zobacz [zasobów w aplikacjach pulpitu](/dotnet/framework/resources/index) w *Przewodnik programistów platformy .NET Framework.* Aby uzyskać informacje na ręczne dodanie do projektów zarządzanych plików zasobów, uzyskiwanie dostępu do zasobów, wyświetlanie zasoby statyczne i przypisanie do właściwości ciągów zasobów, zobacz [tworzenie plików zasobów dla aplikacji pulpitu](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informacje dotyczące globalizacji i lokalizacji zasobów w zarządzanych aplikacjach, zobacz [Globalizing i lokalizacja aplikacji .NET Framework](/dotnet/standard/globalization-localization/index).  
  
## <a name="requirements"></a>Wymagania  
 Win32  
  
## <a name="see-also"></a>Zobacz też  
 [Formanty w oknach dialogowych](../windows/controls-in-dialog-boxes.md)   
 [Kontrolki](../mfc/controls-mfc.md)

