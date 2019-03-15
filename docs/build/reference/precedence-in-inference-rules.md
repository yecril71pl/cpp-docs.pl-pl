---
title: Pierwszeństwo w zasadach wnioskowania
ms.date: 11/04/2016
helpviewer_keywords:
- inference rules in NMAKE
- rules, inference
- precedence, inference rule
ms.assetid: 69e3dc02-0815-4c3a-b02b-1cb85fceaf24
ms.openlocfilehash: ca24134fd1829ad3d97ca67b8c30aae3af4109ee
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57823656"
---
# <a name="precedence-in-inference-rules"></a>Pierwszeństwo w zasadach wnioskowania

Jeśli zasada wnioskowania został zdefiniowany wiele razy, NMAKE używa definicji najwyższy priorytet. Na poniższej liście przedstawiono kolejność pierwszeństwa od najwyższego do najniższego:

1. Reguła wnioskowania zdefiniowane w pliku reguł programu make; nowsze definicje mają pierwszeństwo.

1. Reguła wnioskowania zdefiniowane w Tools.ini; nowsze definicje mają pierwszeństwo.

1. Reguła wnioskowania wstępnie zdefiniowane.

## <a name="see-also"></a>Zobacz także

[Zasady wnioskowania](inference-rules.md)
