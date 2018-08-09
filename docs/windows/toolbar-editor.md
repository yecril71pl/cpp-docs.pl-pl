---
title: Edytor paska narzędzi | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.toolbar.F1
dev_langs:
- C++
helpviewer_keywords:
- resource editors, Toolbar editor
- editors, toolbars
- toolbars [C++], editing
- Toolbar editor
ms.assetid: aa9f0adf-60f6-4f79-ab05-bc330f15ec43
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: fe9c73a09e2a0f220ee4454baefb07b7e65fcafa
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39641650"
---
# <a name="toolbar-editor"></a>Edytor paska narzędzi
Edytor paska narzędzi umożliwia tworzenie zasobów narzędzi i konwertowanie map bitowych na zasoby paska narzędzi. Edytor paska narzędzi wykorzystuje graficzny widok, aby pokazać, narzędzi i przyciski, które przypominają, jak będzie wyglądał w ukończonej aplikacji.  
  
 Edytor paska narzędzi możesz:  
  
-   [Tworzenie nowych pasków narzędzi i przycisków](../windows/creating-new-toolbars.md)  
  
-   [Konwertowanie map bitowych na zasoby paska narzędzi](../windows/converting-bitmaps-to-toolbars.md)  
  
-   [Tworzenie, przenoszenie i edytowanie przycisków paska narzędzi](../windows/creating-moving-and-editing-toolbar-buttons.md)  
  
-   [Tworzenie etykietek narzędzi](../windows/creating-a-tool-tip-for-a-toolbar-button.md)  
  
 Okno Edytor paska narzędzi wyświetla dwa widoki obrazu przycisku, taka sama jak okno edytora obrazów. Pasek podziału rozdziela dwa okienka. Aby zmieniać względne rozmiary okienek, można przeciągać pasek podziału. Aktywne okienko wyświetla krawędź wyboru. Powyższe dwa widoki obrazu jest narzędzi podmiotu.  
  
 ![Edytor paska narzędzi](../mfc/media/vctoolbareditor.gif "vcToolbarEditor")  
Edytor paska narzędzi  
  
 Edytor paska narzędzi jest podobny do edytora obrazów w działaniu. Elementy menu, Narzędzia grafiki i mapy bitowej siatki są takie same, jak w edytorze obrazu. Brak polecenia menu w menu obrazu, aby możliwe było przełączać się między Edytor paska narzędzi i edytora obrazów. Aby uzyskać więcej informacji na temat korzystania z narzędzi graficznych, paleta kolorów lub menu obrazu, zobacz [edytora obrazów](../windows/image-editor-for-icons.md).  
  
 Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Creating Resource Files dla aplikacji klasycznych](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Aby uzyskać informacji na temat globalizacja i lokalizacja zasobów w aplikacjach zarządzanych, zobacz [Globalizing i lokalizowanie aplikacji programu .NET Framework](/dotnet/standard/globalization-localization/index).  
  
## <a name="requirements"></a>Wymagania  
 ATL i MFC  
  
## <a name="see-also"></a>Zobacz też  
 [Edytory zasobów](../windows/resource-editors.md)   
 [Menu i inne zasoby](http://msdn.microsoft.com/library/windows/desktop/ms632583.aspx)