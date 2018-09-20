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
ms.openlocfilehash: c3226df51d2a83484de78d0d76c9af67e150e8eb
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46403191"
---
# <a name="window-procedure-entry-points"></a>Punkty wejścia procedury okna

Aby chronić procedury okna MFC, łączy statycznych modułu, z implementacją procedury okna specjalnego. Powiązanie odbywa się automatycznie, gdy moduł jest połączone z MFC. Ta procedura okna wykorzystuje makro AFX_MANAGE_STATE poprawnie ustawić stan skuteczne modułu, a następnie wywołuje metodę `AfxWndProc`, który z kolei deleguje do `WindowProc` funkcji składowej typu odpowiednie `CWnd`-pochodzi z obiektu.

## <a name="see-also"></a>Zobacz też

[Zarządzanie danymi stanu modułów MFC](../mfc/managing-the-state-data-of-mfc-modules.md)

