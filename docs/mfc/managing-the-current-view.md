---
title: Zarządzanie bieżącym widokiem | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- views [MFC], and OnActivateView method [MFC]
- views [MFC], deactivating
- views [MFC], activating
- frame windows [MFC], current view
- OnActivateView method [MFC]
- views [MFC], current
- deactivating views [MFC]
- current view in frame window [MFC]
ms.assetid: 0a1cc22d-d646-4536-9ad2-3cb6d7092e4a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ca9738f9b6083ef88c2f72e1608121f849f8e909
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46425381"
---
# <a name="managing-the-current-view"></a>Zarządzanie bieżącym widokiem

W ramach domyślna Implementacja klasy okien ramowych okno ramowe przechowuje informacje o aktualnie aktywnego widoku. Jeśli okno ramowe zawiera więcej niż jeden widok, na przykład w okna dzielącego, bieżący widok jest najbardziej aktualną widoku w użyciu. Widok aktywny jest niezależna od aktywnego okna w Windows lub bieżący fokus wprowadzania.

Gdy bieżącym widokiem zmieni, struktura powiadamia bieżący widok, wywołując jego [OnActivateView](../mfc/reference/cview-class.md#onactivateview) funkcja elementu członkowskiego. Można stwierdzić, czy widok jest aktywowany lub dezaktywowany, sprawdzając `OnActivateView`firmy *bActivate* parametru. Domyślnie `OnActivateView` Ustawia fokus na bieżący widok aktywacji. Można zastąpić `OnActivateView` do wykonania dowolnej specjalnego przetwarzania, jeśli widok jest dezaktywowany lub ponownie aktywować. Na przykład możesz chcieć zapewnić specjalne podpowiedzi wizualne do odróżnienia widok aktywny od innych, nieaktywne widoki.

Okno ramowe przekazuje polecenia do bieżącego widoku (aktywny), zgodnie z opisem w [Routing poleceń](../mfc/command-routing.md), w ramach standardowego routingu poleceń.

## <a name="see-also"></a>Zobacz też

[Używanie okien ramowych](../mfc/using-frame-windows.md)

