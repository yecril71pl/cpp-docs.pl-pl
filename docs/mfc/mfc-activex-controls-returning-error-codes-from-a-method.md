---
title: 'Kontrolki ActiveX MFC: Zwracanie kodów błędów z metody'
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], error codes
- SetNotSupported method, using
- errors [MFC], ActiveX control error codes
- GetNotSupported method [MFC]
- FireError method [MFC]
- SCODE, MFC ActiveX controls
- ThrowError method [MFC]
ms.assetid: 771fb9c9-2413-4dcc-b386-7bc4c4adeafd
ms.openlocfilehash: 0800c1827c636dd81e2928e33c0ee2afde4c94ac
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62324275"
---
# <a name="mfc-activex-controls-returning-error-codes-from-a-method"></a>Kontrolki ActiveX MFC: Zwracanie kodów błędów z metody

W tym artykule opisano sposób zwracania kodów błędów z metody formantu ActiveX.

Aby wskazać, wystąpi błąd w obrębie metody, należy użyć [COleControl::ThrowError](../mfc/reference/colecontrol-class.md#throwerror) funkcja elementu członkowskiego, która przyjmuje SCODE (kod stanu), jako parametr. Można użyć wstępnie zdefiniowanych SCODE lub zdefiniować własny.

> [!NOTE]
>  `ThrowError` jest przeznaczona do użycia wyłącznie jako środek zwróci błąd z w ramach właściwości Get lub Set funkcji lub metody automatyzacji. Są to tylko razy, które będą znajdować się program obsługi wyjątków odpowiednie znajduje się na stosie.

Funkcje pomocnicze istnieje dla najbardziej typowych predefiniowanymi SCODEs, takimi jak [COleControl::SetNotSupported](../mfc/reference/colecontrol-class.md#setnotsupported), [COleControl::GetNotSupported](../mfc/reference/colecontrol-class.md#getnotsupported), i [COleControl::SetNotPermitted](../mfc/reference/colecontrol-class.md#setnotpermitted).

Aby uzyskać listę wstępnie zdefiniowanych SCODEs i instrukcje na temat definiowania SCODEs niestandardowych, zobacz sekcję [obsługi błędów w tym formancie ActiveX](../mfc/mfc-activex-controls-advanced-topics.md) w kontrolkach ActiveX: Tematy zaawansowane.

Aby uzyskać więcej informacji na temat raportowania wyjątków w innych obszarach kodu, zobacz [COleControl::FireError](../mfc/reference/colecontrol-class.md#fireerror) oraz sekcję [obsługi błędów w tym formancie ActiveX](../mfc/mfc-activex-controls-advanced-topics.md) w kontrolkach ActiveX: Tematy zaawansowane.

## <a name="see-also"></a>Zobacz także

[Kontrolki ActiveX MFC](../mfc/mfc-activex-controls.md)
