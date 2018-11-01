---
title: Pierwszeństwo w zasadach wnioskowania
ms.date: 11/04/2016
helpviewer_keywords:
- inference rules in NMAKE
- rules, inference
- precedence, inference rule
ms.assetid: 69e3dc02-0815-4c3a-b02b-1cb85fceaf24
ms.openlocfilehash: 30dee54c99115c076f7662bafb8aa22d97f234fa
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50548736"
---
# <a name="precedence-in-inference-rules"></a>Pierwszeństwo w zasadach wnioskowania

Jeśli zasada wnioskowania został zdefiniowany wiele razy, NMAKE używa definicji najwyższy priorytet. Na poniższej liście przedstawiono kolejność pierwszeństwa od najwyższego do najniższego:

1. Reguła wnioskowania zdefiniowane w pliku reguł programu make; nowsze definicje mają pierwszeństwo.

1. Reguła wnioskowania zdefiniowane w Tools.ini; nowsze definicje mają pierwszeństwo.

1. Reguła wnioskowania wstępnie zdefiniowane.

## <a name="see-also"></a>Zobacz też

[Zasady wnioskowania](../build/inference-rules.md)