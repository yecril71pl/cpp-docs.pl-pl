---
title: Pierwszeństwo w definicjach makr
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, precedence in macro definitions
- macros, precedence
ms.assetid: 0c13182d-83cb-4cbd-af2d-f4c916b62aeb
ms.openlocfilehash: 8829b3cdbc7b2324ef3d118f8ca45dd2a1621e7e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50619088"
---
# <a name="precedence-in-macro-definitions"></a>Pierwszeństwo w definicjach makr

Jeśli makro ma wiele definicji, NMAKE używa definicji najwyższy priorytet. Na poniższej liście przedstawiono kolejność pierwszeństwa od najwyższego do najniższego:

1. Makra zdefiniowane w wierszu polecenia

1. Makra zdefiniowane w pliku reguł programu make lub Dołącz plik

1. Odziedziczone makra zmiennych środowiskowych

1. Makra zdefiniowane w pliku Tools.ini

1. Wstępnie zdefiniowane makro, takich jak [DW](../build/command-macros-and-options-macros.md) i [AS](../build/command-macros-and-options-macros.md)

/E umożliwia powodują, że makra odziedziczone zmiennych środowiskowych w celu zastąpienia pliku reguł programu make makra o takiej samej nazwie. Użyj **! UNDEF** do zastąpienia wiersza polecenia.

## <a name="see-also"></a>Zobacz też

[Definiowanie makro NMAKE](../build/defining-an-nmake-macro.md)