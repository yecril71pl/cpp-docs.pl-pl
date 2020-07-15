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
ms.openlocfilehash: b2ff9929de74d99fbc45e4f4ff38fd6b939697bc
ms.sourcegitcommit: 31a443c9998cf5cfbaff00fcf815b133f55b2426
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/14/2020
ms.locfileid: "86373830"
---
# <a name="highentropyva"></a>/HIGHENTROPYVA

Określa, czy obraz wykonywalny obsługuje generowanie losowe układu przestrzeni adresowej o wysokiej entropii 64 (ASLR).

## <a name="syntax"></a>Składnia

> **/HIGHENTROPYVA**[**: No**]

## <a name="remarks"></a>Uwagi

Ta opcja modyfikuje nagłówek *obrazu wykonywalnego*, pliku. dll lub pliku. exe, aby wskazać, czy obsługiwane są ASLR z adresami 64-bitowymi. Gdy ta opcja jest ustawiona dla pliku wykonywalnego i wszystkich modułów, od których jest zależna, system operacyjny obsługujący 64-bitowy ASLR może odtworzyć segmenty obrazu wykonywalnego w czasie ładowania przy użyciu losowych adresów w 64-bitowej wirtualnej przestrzeni adresowej. Ta duża przestrzeń adresowa utrudnia osobie atakującej odpuszczenie lokalizacji określonego obszaru pamięci.

Domyślnie konsolidator włącza **/HIGHENTROPYVA** na 64-bitowe obrazy wykonywalne. Ta opcja wymaga [/LARGEADDRESSAWARE](largeaddressaware.md), który jest również domyślnie włączony dla obrazów 64-bitowych. **/HIGHENTROPYVA** nie ma zastosowania do 32-bitowych obrazów wykonywalnych, w których opcja jest ignorowana. Aby jawnie wyłączyć tę opcję, użyj **/HIGHENTROPYVA: No**. Aby ta opcja miała efekt, należy również ustawić opcję [/DYNAMICBASE](dynamicbase.md) .

## <a name="see-also"></a>Zobacz też

- [Opcje polecenia EDITBIN](editbin-options.md)
- [/DYNAMICBASE](dynamicbase.md)
- [Ochrona przed oprogramowaniem ISV systemu Windows](https://docs.microsoft.com/previous-versions/bb430720(v=msdn.10))
