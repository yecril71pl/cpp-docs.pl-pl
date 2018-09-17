---
title: Pierwszeństwo w definicjach makr | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- NMAKE program, precedence in macro definitions
- macros, precedence
ms.assetid: 0c13182d-83cb-4cbd-af2d-f4c916b62aeb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 21a3d8873fd1fee61afec865181bab27305bebfd
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45722218"
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