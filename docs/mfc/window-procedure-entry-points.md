---
title: Punkty wejścia procedury okna | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- state management, window procedures
- MFC, managing state data
- window procedure entry points
- entry points, window procedures
ms.assetid: a6b46a7f-6e42-45f2-9ae6-82e19fc57148
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1095061cce8ff8f189984aca99a06eb741a46e83
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33382076"
---
# <a name="window-procedure-entry-points"></a>Punkty wejścia procedury okna
Aby chronić procedury okna MFC, statycznych łączy modułu, z implementacją procedury specjalne okno. Powiązanie odbywa się automatycznie, gdy moduł jest połączony z MFC. Korzysta z tej procedury okna `AFX_MANAGE_STATE` makra, aby poprawnie ustawić stan modułu skuteczne, a następnie wywołuje **AfxWndProc**, który z kolei deleguje do `WindowProc` funkcji członkowskiej klasy odpowiednie `CWnd`-pochodnych obiekt.  
  
## <a name="see-also"></a>Zobacz też  
 [Zarządzanie danymi stanu modułów MFC](../mfc/managing-the-state-data-of-mfc-modules.md)

