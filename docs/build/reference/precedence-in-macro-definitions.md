---
title: Pierwszeństwo w definicjach makr
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, precedence in macro definitions
- macros, precedence
ms.assetid: 0c13182d-83cb-4cbd-af2d-f4c916b62aeb
ms.openlocfilehash: 38a653a9f460beae81f9f88ea457870d30f25339
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62320165"
---
# <a name="precedence-in-macro-definitions"></a>Pierwszeństwo w definicjach makr

Jeśli makro ma wiele definicji, NMAKE używa definicji najwyższy priorytet. Na poniższej liście przedstawiono kolejność pierwszeństwa od najwyższego do najniższego:

1. Makra zdefiniowane w wierszu polecenia

1. Makra zdefiniowane w pliku reguł programu make lub Dołącz plik

1. Odziedziczone makra zmiennych środowiskowych

1. Makra zdefiniowane w pliku Tools.ini

1. Wstępnie zdefiniowane makro, takich jak [DW](command-macros-and-options-macros.md) i [AS](command-macros-and-options-macros.md)

/E umożliwia powodują, że makra odziedziczone zmiennych środowiskowych w celu zastąpienia pliku reguł programu make makra o takiej samej nazwie. Użyj **! UNDEF** do zastąpienia wiersza polecenia.

## <a name="see-also"></a>Zobacz także

[Definiowanie makro NMAKE](defining-an-nmake-macro.md)
