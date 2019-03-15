---
title: Bloki opisów
ms.date: 11/04/2016
helpviewer_keywords:
- description blocks
- NMAKE program, description blocks
- blocks, description
ms.assetid: 1321f228-d389-40ac-b0cd-4f6e9293602b
ms.openlocfilehash: da9265d6b0026bb47496d3aa58847824b5d634d2
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57823881"
---
# <a name="description-blocks"></a>Bloki opisów

Blok opis znajduje się w wierszu zależności, opcjonalnie, blok poleceń:

```
targets... : dependents...
    commands...
```

Wiersz zależności określa jeden lub więcej obiektów docelowych i zero lub więcej elementów zależnych. Obiekt docelowy musi być na początku wiersza. Oddzielne obiekty docelowe z zależności za pomocą dwukropka (:); spacje lub tabulatory są dozwolone. Podział wiersza, należy użyć kreski ułamkowej odwróconej (\) po docelowego lub zależnych od ustawień lokalnych. Jeśli obiekt docelowy nie istnieje, ma sygnaturą czasową wcześniejszych niż zależnych od ustawień lokalnych lub jest [pseudotarget](pseudotargets.md), NMAKE wykonuje polecenia. Jeśli zależnych od ustawień lokalnych jest ona lokalizacją docelową, gdzie indziej i nie istnieje lub jest nieaktualna w odniesieniu do jego własnej zależności NMAKE aktualizacji zależnych od ustawień lokalnych przed rozpoczęciem aktualizacji bieżący zależności.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat?

[Docelowe elementy](targets.md)

[Zależności](dependents.md)

## <a name="see-also"></a>Zobacz także

[NMAKE — dokumentacja](nmake-reference.md)
