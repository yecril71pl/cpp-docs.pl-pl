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
ms.openlocfilehash: 5314545a3a903158362dbfa65c4a9a1b2143e86b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364559"
---
# <a name="mfc-activex-controls-returning-error-codes-from-a-method"></a>Formanty MFC ActiveX: zwracanie kodów błędów z metody

W tym artykule opisano sposób zwracania kodów błędów z metody kontroli ActiveX.

Aby wskazać, że wystąpił błąd w ramach metody, należy użyć [COleControl::ThrowError](../mfc/reference/colecontrol-class.md#throwerror) funkcji elementu członkowskiego, który przyjmuje SCODE (kod stanu) jako parametr. Można użyć wstępnie zdefiniowanego kodu SCODE lub zdefiniować jeden z własnych.

> [!NOTE]
> `ThrowError`jest przeznaczony do użycia tylko jako środek zwracania błędu z wewnątrz właściwości Get lub Set funkcji lub metody automatyzacji. Są to tylko razy, że odpowiedni program obsługi wyjątków będzie obecny na stosie.

Funkcje pomocnika istnieją dla najpopularniejszych wstępnie zdefiniowanych SCODE, takich jak [COleControl::SetNotSupported](../mfc/reference/colecontrol-class.md#setnotsupported), [COleControl::GetNotSupported](../mfc/reference/colecontrol-class.md#getnotsupported)i [COleControl::SetNotPermitted](../mfc/reference/colecontrol-class.md#setnotpermitted).

Aby uzyskać listę wstępnie zdefiniowanych scodees i instrukcje dotyczące definiowania niestandardowych SCODEs, zobacz [sekcję Obsługa błędów w formancie ActiveX](../mfc/mfc-activex-controls-advanced-topics.md) w ActiveX Controls: Advanced Topics.

Aby uzyskać więcej informacji na temat raportowania wyjątków w innych obszarach kodu, zobacz [COleControl::FireError](../mfc/reference/colecontrol-class.md#fireerror) i sekcji [Obsługi błędów w formancie ActiveX](../mfc/mfc-activex-controls-advanced-topics.md) w ActiveX Formanty: Zaawansowane tematy.

## <a name="see-also"></a>Zobacz też

[Kontrolki ActiveX MFC](../mfc/mfc-activex-controls.md)
