---
title: Wstępnie zdefiniowane symbole ATL
ms.date: 02/14/2019
helpviewer_keywords:
- symbols [C++], ATL predefined
- ATL symbols
ms.assetid: 60d8f4e6-6ed9-47f3-9051-e4bf34384456
ms.openlocfilehash: 6e876fe27bd57194513f637fda90845ca68c59ee
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "59033933"
---
# <a name="atl-predefined-symbols"></a>Wstępnie zdefiniowane symbole ATL

Te symbole są zdefiniowane w plikach nagłówkowych ATL, ale obsługują standardowe funkcje aplikacji Windows i akcje. Te symbole są głównie używane z okien dialogowych.

Podczas pracy z okien dialogowych i formantów w [Edytor okien dialogowych](../windows/dialog-editor.md), te symbole pojawią się w [okno właściwości](/visualstudio/ide/reference/properties-window) skojarzone z wspólnych formantów. Na przykład jeśli Twoje okno dialogowe ma **anulować** przycisk, polecenie będzie skojarzona z symbolem IDCANCEL w **właściwości** okna.

|||
|-|-|
|IDABORT|(formant) Okno dialogowe, przycisk Przerwij|
|IDC_STATIC|(formant) Formant statyczny|
|IDCANCEL|(formant) Okno dialogowe, przycisk Anuluj|
|IDIGNORE|(formant) Okno dialogowe, przycisk Ignoruj|
|IDNO|(formant) Okno dialogowe, ma przycisku|
|IDOK|(formant) Okno dialogowe, przycisk OK|
|IDR_ACCELERATOR1|(zasób) Tabela akceleratora|
|IDRETRY|(formant) Okno dialogowe, przycisk Ponów próbę|
|IDS_PROJNAME|(string) Bieżąca nazwa aplikacji|
|IDYES|(formant) Okno dialogowe, przycisk Tak|

## <a name="requirements"></a>Wymagania

ATL

## <a name="see-also"></a>Zobacz także

[Wstępnie zdefiniowane symbole identyfikatorów](../windows/predefined-symbol-ids.md)<br/>
[Wstępnie zdefiniowane symbole MFC](../windows/mfc-predefined-symbols.md)<br/>
[Wstępnie zdefiniowane symbole Win32](../windows/win32-predefined-symbols.md)<br/>