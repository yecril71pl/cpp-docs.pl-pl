---
title: Punkty wejścia procedury okna
ms.date: 11/04/2016
helpviewer_keywords:
- state management, window procedures
- MFC, managing state data
- window procedure entry points
- entry points, window procedures
ms.assetid: a6b46a7f-6e42-45f2-9ae6-82e19fc57148
ms.openlocfilehash: 6d91e2c432588afc5a84f7189fa87a7fc2531b1a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62372015"
---
# <a name="window-procedure-entry-points"></a>Punkty wejścia procedury okna

Aby chronić procedury okna MFC, łączy statycznych modułu, z implementacją procedury okna specjalnego. Powiązanie odbywa się automatycznie, gdy moduł jest połączone z MFC. Ta procedura okna wykorzystuje makro AFX_MANAGE_STATE poprawnie ustawić stan skuteczne modułu, a następnie wywołuje metodę `AfxWndProc`, który z kolei deleguje do `WindowProc` funkcji składowej typu odpowiednie `CWnd`-pochodzi z obiektu.

## <a name="see-also"></a>Zobacz także

[Zarządzanie danymi stanu modułów MFC](../mfc/managing-the-state-data-of-mfc-modules.md)
