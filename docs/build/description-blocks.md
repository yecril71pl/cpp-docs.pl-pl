---
title: Bloki opisów
ms.date: 11/04/2016
helpviewer_keywords:
- description blocks
- NMAKE program, description blocks
- blocks, description
ms.assetid: 1321f228-d389-40ac-b0cd-4f6e9293602b
ms.openlocfilehash: 214963b5c3f633e8d029cee0500d4bd5fab6ed53
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50490613"
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