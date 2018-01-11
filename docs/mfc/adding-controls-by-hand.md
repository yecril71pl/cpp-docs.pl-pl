---
title: "Dodawanie formantów ręcznie | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- Windows common controls [MFC], adding
- dialog box controls [MFC], adding to dialog boxes
- controlling input focus
- input focus control
- focus, controlling input [MFC]
- controls [MFC], adding to dialog boxes
- common controls [MFC], adding
ms.assetid: bc843e59-0c51-4b5b-8bf2-343f716469d2
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b13f6fdfb3c11819eb8d8838e5617e7a349d1023
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="adding-controls-by-hand"></a>Ręczne dodawanie formantów
Możesz albo [dodawanie formantów do okna dialogowego z edytora okien dialogowych](../mfc/using-the-dialog-editor-to-add-controls.md) lub dodawać je samodzielnie, z kodem.  
  
 Aby utworzyć obiekt formantu samodzielnie, będzie zazwyczaj osadzić C++ obiekt formantu w oknie dialogowym C++ lub obiektu okna ramowego. Podobnie jak wiele innych obiektów w ramach formanty wymagają dwuetapowa konstrukcja. Należy wywołać formantu **Utwórz** funkcji członkowskiej podczas tworzenia okna dialogowego pola lub ramki okno nadrzędne. W oknach dialogowych, zwykle odbywa się [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog)i okna ramowe w [OnCreate](../mfc/reference/cwnd-class.md#oncreate).  
  
 W poniższym przykładzie pokazano, jak mogą zadeklarować `CEdit` obiektu w deklaracji klasy, klasy pochodnej okna dialogowego, a następnie wywołać **Utwórz** funkcji członkowskiej we `OnInitDialog`. Ponieważ `CEdit` obiektu jest zadeklarowany jako osadzonego obiektu, jest automatycznie tworzony, podczas konstruowania obiektu okna dialogowego, ale nadal musi zostać zainicjowany z własną **Utwórz** funkcję elementu członkowskiego.  
  
 [!code-cpp[NVC_MFCControlLadenDialog#1](../mfc/codesnippet/cpp/adding-controls-by-hand_1.h)]  
  
 Następujące `OnInitDialog` funkcja ustawia prostokąt, następnie wywołuje **Utwórz** do tworzenia kontrolki edycji systemu Windows i dołącz je do niezainicjowanego `CEdit` obiektu.  
  
 [!code-cpp[NVC_MFCControlLadenDialog#2](../mfc/codesnippet/cpp/adding-controls-by-hand_2.cpp)]  
  
 Po utworzeniu obiektu edycji można również ustawić fokus wprowadzania do formantu przez wywołanie metody `SetFocus` funkcję elementu członkowskiego. Na koniec wróć 0 z `OnInitDialog` do wyświetlenia, aby ustawić fokus. Jeśli zwróci wartość niezerową, okno dialogowe menedżera Ustawia fokus do pierwszego elementu kontrolki w oknie dialogowym listy elementów. W większości przypadków należy Dodaj formanty do Twojej okien dialogowych z edytora okien dialogowych.  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie i używanie formantów](../mfc/making-and-using-controls.md)   
 [Formanty](../mfc/controls-mfc.md)   
 [CDialog::OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog)

