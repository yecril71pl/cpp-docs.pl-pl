---
title: "Punkty wejścia procedury okna | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- state management, window procedures
- MFC, managing state data
- window procedure entry points
- entry points, window procedures
ms.assetid: a6b46a7f-6e42-45f2-9ae6-82e19fc57148
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5f4e99ce38bd5ae472d688dc779bdd4ccf9fd4c5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="window-procedure-entry-points"></a>Punkty wejścia procedury okna
Aby chronić procedury okna MFC, statycznych łączy modułu, z implementacją procedury specjalne okno. Powiązanie odbywa się automatycznie, gdy moduł jest połączony z MFC. Korzysta z tej procedury okna `AFX_MANAGE_STATE` makra, aby poprawnie ustawić stan modułu skuteczne, a następnie wywołuje **AfxWndProc**, który z kolei deleguje do `WindowProc` funkcji członkowskiej klasy odpowiednie `CWnd`-pochodnych obiekt.  
  
## <a name="see-also"></a>Zobacz też  
 [Zarządzanie danymi stanu modułów MFC](../mfc/managing-the-state-data-of-mfc-modules.md)

