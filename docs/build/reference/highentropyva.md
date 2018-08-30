---
title: -HIGHENTROPYVA | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 06/12/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /HIGHENTROPYVA
dev_langs:
- C++
helpviewer_keywords:
- HIGHENTROPYVA editbin option
- -HIGHENTROPYVA editbin option
- /HIGHENTROPYVA editbin option
ms.assetid: ef4b7c63-440d-40ca-b39d-edefb3217505
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5fec9314be9d69e2cb0af2a98884bd78de1ff679
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43211689"
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
