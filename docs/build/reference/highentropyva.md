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
ms.openlocfilehash: 80e34a3f57974e1af6afb65196697cce9aa344b1
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88835002"
---
# <a name="highentropyva"></a>/HIGHENTROPYVA

Określa, czy obraz wykonywalny obsługuje generowanie losowe układu przestrzeni adresowej o wysokiej entropii 64 (ASLR).

## <a name="syntax"></a>Składnia

> **`/HIGHENTROPYVA`**[**`:NO`**]

## <a name="remarks"></a>Uwagi

Ta opcja modyfikuje nagłówek pliku *obrazu wykonywalnego* (na przykład *`.dll`* *`.exe`* plik lub), aby wskazać obsługę 64-bitowego adresu ASLR. Aby mieć efekt, należy ustawić opcję zarówno dla pliku wykonywalnego, jak i wszystkich modułów, od których jest zależna. Następnie systemy operacyjne obsługujące 64-bitowe ASLR mogą odtworzyć segmenty obrazu wykonywalnego w czasie ładowania przy użyciu losowych, 64-bitowych adresów wirtualnych. Ta duża przestrzeń adresowa utrudnia osobie atakującej odpuszczenie lokalizacji określonego obszaru pamięci.

Domyślnie konsolidator włącza **`/HIGHENTROPYVA`** 64-bitowe obrazy wykonywalne. Ta opcja wymaga zarówno [`/DYNAMICBASE`](dynamicbase.md) programu, jak i [`/LARGEADDRESSAWARE`](largeaddressaware.md) , które są również domyślnie włączone dla obrazów 64-bitowych. **`/HIGHENTROPYVA`** nie dotyczy 32-bitowych obrazów plików wykonywalnych, w których opcja jest ignorowana. Aby jawnie wyłączyć tę opcję, użyj **`/HIGHENTROPYVA:NO`** .

## <a name="see-also"></a>Zobacz też

[Opcje polecenia EDITBIN](editbin-options.md)\
[`/DYNAMICBASE`](dynamicbase.md)\
[`/LARGEADDRESSAWARE`](largeaddressaware.md)\
[Ochrona przed oprogramowaniem ISV systemu Windows](/previous-versions/bb430720(v=msdn.10))
