---
title: Wstępnie zdefiniowane symbole ATL | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- symbols [C++], ATL predefined
- ATL symbols
ms.assetid: 60d8f4e6-6ed9-47f3-9051-e4bf34384456
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6b1ee8da2ea13eb5a095193af94a9253e53c865f
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44318008"
---
# <a name="atl-predefined-symbols"></a>Wstępnie zdefiniowane symbole ATL

Te symbole są zdefiniowane w plikach nagłówkowych ATL, ale obsługują standardowe funkcje aplikacji Windows i akcje. Te symbole są głównie używane z okien dialogowych. Podczas pracy z okien dialogowych i formantów w [Edytor okien dialogowych](../windows/dialog-editor.md), te symbole pojawią się w **właściwości** skojarzone z wspólnych formantów okna. Na przykład jeśli Twoje okno dialogowe ma **anulować** przycisk, polecenie będzie skojarzona z symbolem IDCANCEL w [okno właściwości](/visualstudio/ide/reference/properties-window).

|||
|-|-|
|IDABORT|Sterowania: Przycisk Przerwij pola okna dialogowego|
|IDC_STATIC|Kontrolki: Formant statyczny|
|IDCANCEL|Sterowania: Przycisk Anuluj okno dialogowe|
|IDIGNORE|Sterowania: Przycisk Ignoruj pola dialogowe|
|IDNO|Sterowania: Okno dialogowe ma przycisku|
|IDOK|Sterowania: Przycisk pola OK okno dialogowe|
|IDR_ACCELERATOR1|Zasobów: Tabela akceleratora|
|IDRETRY|Sterowania: Przycisk Ponów okno dialogowe|
|IDS_PROJNAME|Ciąg: Bieżąca nazwa aplikacji|
|IDYES|Kontrola: Okno dialogowe tak przycisku.|

## <a name="requirements"></a>Wymagania

ATL

## <a name="see-also"></a>Zobacz też

[Wstępnie zdefiniowane identyfikatory symboli](../windows/predefined-symbol-ids.md)  
[Symbole: identyfikatory zasobów](../windows/symbols-resource-identifiers.md)