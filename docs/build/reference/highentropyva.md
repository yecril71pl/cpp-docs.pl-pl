---
title: /HIGHENTROPYVA
ms.date: 06/12/2018
f1_keywords:
- /HIGHENTROPYVA
helpviewer_keywords:
- HIGHENTROPYVA editbin option
- -HIGHENTROPYVA editbin option
- /HIGHENTROPYVA editbin option
ms.assetid: ef4b7c63-440d-40ca-b39d-edefb3217505
ms.openlocfilehash: 90d3c868eaab85e3b1a2a416c9aa14b0e27ec8f9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50603986"
---
# <a name="highentropyva"></a>/HIGHENTROPYVA

Określa, czy obraz wykonywalny obsługuje z randomizacji układu przestrzeni adresowej 64-bitowej o wysokiej entropii (ASLR).

## <a name="syntax"></a>Składnia

> **/ HIGHENTROPYVA**[**: NO**]

## <a name="remarks"></a>Uwagi

Ta opcja modyfikuje nagłówek *obrazu pliku wykonywalnego*, pliku .dll lub pliku .exe, aby wskazać czy obsługiwany jest ASLR z 64-bitowymi adresami. Gdy ta opcja jest ustawiona na wykonawczą i wszystkie moduły, w których jest zależna, system operacyjny, który obsługuje 64-bitowy ASLR może przemieścić segmenty wykonawczego obrazu w czasie ładowania, używając niestandardowych adresów w 64-bitowej wirtualnej przestrzeni adresowej. Ta duża przestrzeń na sprawia, że utrudnia osobie atakującej intruzowi zgadnąć lokalizację konkretnego regionu pamięci.

Domyślnie, włącza konsolidator **/highentropyva** dla 64-bitowych obrazów wykonywalnych. Ta opcja wymaga [/largeaddressaware](largeaddressaware.md), który jest również domyślnie włączone dla 64-bitowych obrazów. **/ HIGHENTROPYVA** nie ma zastosowania do wykonywalnych obrazów 32-bitowych, gdy opcja jest ignorowana. Aby jawnie wyłączyć tę opcję, należy użyć **/HIGHENTROPYVA:NO**. Aby uzyskać tę opcję, aby mieć wpływ [opcja/DynamicBase](dynamicbase.md) opcja musi być ustawiona.

## <a name="see-also"></a>Zobacz także

- [Opcje EDITBIN](editbin-options.md)
- [/DYNAMICBASE](dynamicbase.md)
- [Poziom ochrony oprogramowania niezależnego dostawcy oprogramowania Windows](https://msdn.microsoft.com/library/bb430720.aspx)
