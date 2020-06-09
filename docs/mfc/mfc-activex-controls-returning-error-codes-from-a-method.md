---
title: 'Formanty MFC ActiveX: zwracanie kodów błędów z metody'
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
ms.openlocfilehash: 1f7564d750b476ac3f57656f3392e0801652e5d5
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84615514"
---
# <a name="mfc-activex-controls-returning-error-codes-from-a-method"></a>Formanty MFC ActiveX: zwracanie kodów błędów z metody

W tym artykule opisano, jak zwrócić kody błędów z metody kontrolki ActiveX.

Aby wskazać, że wystąpił błąd w metodzie, należy użyć funkcji składowej [COleControl:: ThrowError](reference/colecontrol-class.md#throwerror) , która przyjmuje jako parametr SCODE (kod stanu). Możesz użyć wstępnie zdefiniowanego SCODE lub zdefiniować jeden z nich.

> [!NOTE]
> `ThrowError`ma być używany tylko jako środek zwrócenia błędu z funkcji get lub set właściwości lub metody automatyzacji. Są to jedyne sytuacje, w których na stosie będzie obecny odpowiedni program obsługi wyjątków.

Istnieją funkcje pomocnika dla najpopularniejszych wstępnie zdefiniowanych SCODEs, takich jak [COleControl:: SetNotSupported](reference/colecontrol-class.md#setnotsupported), [COleControl:: GetNotSupported](reference/colecontrol-class.md#getnotsupported)i [COleControl:: SetNotPermitted](reference/colecontrol-class.md#setnotpermitted).

Aby zapoznać się z listą wstępnie zdefiniowanych SCODEs i instrukcji dotyczących definiowania niestandardowych SCODEs, zobacz sekcję [Obsługa błędów w kontrolce ActiveX](mfc-activex-controls-advanced-topics.md) w kontrolkach ActiveX: Tematy zaawansowane.

Aby uzyskać więcej informacji na temat raportowania wyjątków w innych obszarach kodu, zobacz [COleControl:: FireError —](reference/colecontrol-class.md#fireerror) i sekcja [Obsługa błędów w kontrolce ActiveX](mfc-activex-controls-advanced-topics.md) w kontrolkach ActiveX: Tematy zaawansowane.

## <a name="see-also"></a>Zobacz też

[Kontrolki ActiveX MFC](mfc-activex-controls.md)
