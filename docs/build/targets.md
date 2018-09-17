---
title: Obiekty docelowe | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- targets, specifying in NMAKE
ms.assetid: 826ee849-4278-4c6e-97c3-79a2b5fe6463
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: edb75258c548526c68ed33f7f8037656750f6855
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45713809"
---
# <a name="targets"></a>Obiekty docelowe

W wierszu zależności, należy określić jeden lub więcej obiektów docelowych, przy użyciu dowolnego prawidłową nazwę pliku, nazwę katalogu lub [pseudotarget](../build/pseudotargets.md). Oddziel wiele elementów docelowych miejsca do magazynowania lub karty. Elementy docelowe nie jest uwzględniana wielkość liter. Ścieżki są dozwolone z nazwami plików. Element docelowy nie może przekraczać 256 znaków. Jeśli element docelowy poprzedza dwukropek jest pojedynczy znak, użyj oddzielający miejsca; w przeciwnym razie NMAKE interpretuje kombinacji dwukropek litery jako specyfikatora dysku.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat?

[Pseudo cele](../build/pseudotargets.md)

[Wiele obiektów docelowych](../build/multiple-targets.md)

[Zależności zbiorcze](../build/cumulative-dependencies.md)

[Obiekty docelowe w blokach opisów](../build/targets-in-multiple-description-blocks.md)

[Skutki uboczne zależności](../build/dependency-side-effects.md)

## <a name="see-also"></a>Zobacz też

[Bloki opisów](../build/description-blocks.md)