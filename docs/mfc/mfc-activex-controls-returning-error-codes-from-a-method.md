---
title: 'Kontrolki ActiveX MFC: Zwracanie kodów błędów z metody | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], error codes
- SetNotSupported method, using
- errors [MFC], ActiveX control error codes
- GetNotSupported method [MFC]
- FireError method [MFC]
- SCODE, MFC ActiveX controls
- ThrowError method [MFC]
ms.assetid: 771fb9c9-2413-4dcc-b386-7bc4c4adeafd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9daaa86f6f57d28b56a7374ff64b0fcbca2a3d98
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46383600"
---
# <a name="mfc-activex-controls-returning-error-codes-from-a-method"></a>Kontrolki ActiveX MFC: zwracanie kodów błędów z metody

W tym artykule opisano sposób zwracania kodów błędów z metody formantu ActiveX.

Aby wskazać, wystąpi błąd w obrębie metody, należy użyć [COleControl::ThrowError](../mfc/reference/colecontrol-class.md#throwerror) funkcja elementu członkowskiego, która przyjmuje SCODE (kod stanu), jako parametr. Można użyć wstępnie zdefiniowanych SCODE lub zdefiniować własny.

> [!NOTE]
>  `ThrowError` jest przeznaczona do użycia wyłącznie jako środek zwróci błąd z w ramach właściwości Get lub Set funkcji lub metody automatyzacji. Są to tylko razy, które będą znajdować się program obsługi wyjątków odpowiednie znajduje się na stosie.

Funkcje pomocnicze istnieje dla najbardziej typowych predefiniowanymi SCODEs, takimi jak [COleControl::SetNotSupported](../mfc/reference/colecontrol-class.md#setnotsupported), [COleControl::GetNotSupported](../mfc/reference/colecontrol-class.md#getnotsupported), i [COleControl::SetNotPermitted](../mfc/reference/colecontrol-class.md#setnotpermitted).

Aby uzyskać listę wstępnie zdefiniowanych SCODEs i instrukcje na temat definiowania SCODEs niestandardowych, zobacz sekcję [obsługi błędów w tym formancie ActiveX](../mfc/mfc-activex-controls-advanced-topics.md) w kontrolkach ActiveX: zaawansowanych tematów.

Aby uzyskać więcej informacji na temat raportowania wyjątków w innych obszarach kodu, zobacz [COleControl::FireError](../mfc/reference/colecontrol-class.md#fireerror) oraz sekcję [obsługi błędów w tym formancie ActiveX](../mfc/mfc-activex-controls-advanced-topics.md) w kontrolkach ActiveX: Tematy zaawansowane.

## <a name="see-also"></a>Zobacz też

[Kontrolki ActiveX MFC](../mfc/mfc-activex-controls.md)

