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
ms.openlocfilehash: 99a4cf3fe356cf888101935aba5bec9a599135f9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="window-procedure-entry-points"></a>Punkty wejścia procedury okna
Aby chronić procedury okna MFC, statycznych łączy modułu, z implementacją procedury specjalne okno. Powiązanie odbywa się automatycznie, gdy moduł jest połączony z MFC. Korzysta z tej procedury okna `AFX_MANAGE_STATE` makra, aby poprawnie ustawić stan modułu skuteczne, a następnie wywołuje **AfxWndProc**, który z kolei deleguje do `WindowProc` funkcji członkowskiej klasy odpowiednie `CWnd`-pochodnych obiekt.  
  
## <a name="see-also"></a>Zobacz też  
 [Zarządzanie danymi stanu modułów MFC](../mfc/managing-the-state-data-of-mfc-modules.md)

