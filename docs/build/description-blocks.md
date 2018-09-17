---
title: Bloki opisów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- description blocks
- NMAKE program, description blocks
- blocks, description
ms.assetid: 1321f228-d389-40ac-b0cd-4f6e9293602b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d83e010f690f96afa5a57eb89ca1e8f4cf444225
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45699663"
---
# <a name="description-blocks"></a>Bloki opisów

Blok opis znajduje się w wierszu zależności, opcjonalnie, blok poleceń:

```
targets... : dependents...
    commands...
```

Wiersz zależności określa jeden lub więcej obiektów docelowych i zero lub więcej elementów zależnych. Obiekt docelowy musi być na początku wiersza. Oddzielne obiekty docelowe z zależności za pomocą dwukropka (:); spacje lub tabulatory są dozwolone. Podział wiersza, należy użyć kreski ułamkowej odwróconej (\) po docelowego lub zależnych od ustawień lokalnych. Jeśli obiekt docelowy nie istnieje, ma sygnaturą czasową wcześniejszych niż zależnych od ustawień lokalnych lub jest [pseudotarget](../build/pseudotargets.md), NMAKE wykonuje polecenia. Jeśli zależnych od ustawień lokalnych jest ona lokalizacją docelową, gdzie indziej i nie istnieje lub jest nieaktualna w odniesieniu do jego własnej zależności NMAKE aktualizacji zależnych od ustawień lokalnych przed rozpoczęciem aktualizacji bieżący zależności.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat?

[Docelowe elementy](../build/targets.md)

[Zależności](../build/dependents.md)

## <a name="see-also"></a>Zobacz też

[NMAKE — dokumentacja](../build/nmake-reference.md)