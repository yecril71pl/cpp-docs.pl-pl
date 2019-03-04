---
title: Używanie niestandardowych ciągów formatu w formancie selektora dat i godzin
ms.date: 11/04/2016
helpviewer_keywords:
- CDateTimeCtrl class [MFC], display styles
- DateTimePicker control [MFC], display styles
- DateTimePicker control [MFC]
ms.assetid: 7d577f03-6ca0-4597-9093-50b78f304719
ms.openlocfilehash: 8da5ecaf473d6d3c35ddc1b95ac856ce8c12f163
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57286889"
---
# <a name="using-custom-format-strings-in-a-date-and-time-picker-control"></a>Używanie niestandardowych ciągów formatu w formancie selektora dat i godzin

Domyślnie formant selektora daty i godziny udostępniają trzy formatowania typy (każdego odpowiadającego stylu unikatowy format) do wyświetlania bieżącej daty lub godziny:

- **DTS_LONGDATEFORMAT** Wyświetla datę w formacie długim, generuje danych wyjściowych, takich jak "Środa, 3 styczeń 2000".

- **DTS_SHORTDATEFORMAT** Wyświetla datę w formacie krótkiej, generuje danych wyjściowych, takich jak "00-1-3".

- **DTS_TIMEFORMAT** Wyświetla godzinę w formacie długim, generuje danych wyjściowych, takich jak "17:31:42: 00".

Można jednak dostosować wygląd daty lub godziny, przy użyciu ciągu formatu niestandardowego. Ten ciąg niestandardowego składa się z istniejących formatów znaków, znaków nonformat lub jako kombinację obu tych. Po skompilowaniu niestandardowy ciąg wywołania [CDateTimeCtrl::SetFormat](../mfc/reference/cdatetimectrl-class.md#setformat) przekazując tekst niestandardowy. Kontrolka selektora daty i godziny będzie wyświetlana bieżąca wartość przy użyciu ciągu formatu niestandardowego.

Poniższy przykład kodu (gdzie *m_dtPicker* jest `CDateTimeCtrl` obiektu) przedstawia jedno z możliwych rozwiązań:

[!code-cpp[NVC_MFCControlLadenDialog#7](../mfc/codesnippet/cpp/using-custom-format-strings-in-a-date-and-time-picker-control_1.cpp)]

Oprócz ciągów formatów niestandardowych, selektor daty i godziny kontroluje również obsługę [pól wywołania zwrotnego](../mfc/using-callback-fields-in-a-date-and-time-picker-control.md).

## <a name="see-also"></a>Zobacz także

[Korzystanie z CDateTimeCtrl](../mfc/using-cdatetimectrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)
