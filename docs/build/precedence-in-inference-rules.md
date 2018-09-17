---
title: Pierwszeństwo w zasadach wnioskowania | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- inference rules in NMAKE
- rules, inference
- precedence, inference rule
ms.assetid: 69e3dc02-0815-4c3a-b02b-1cb85fceaf24
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b4f2e7ff55e935b7e425b552ba85f47f134c6b80
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45725234"
---
# <a name="precedence-in-inference-rules"></a>Pierwszeństwo w zasadach wnioskowania

Jeśli zasada wnioskowania został zdefiniowany wiele razy, NMAKE używa definicji najwyższy priorytet. Na poniższej liście przedstawiono kolejność pierwszeństwa od najwyższego do najniższego:

1. Reguła wnioskowania zdefiniowane w pliku reguł programu make; nowsze definicje mają pierwszeństwo.

1. Reguła wnioskowania zdefiniowane w Tools.ini; nowsze definicje mają pierwszeństwo.

1. Reguła wnioskowania wstępnie zdefiniowane.

## <a name="see-also"></a>Zobacz też

[Zasady wnioskowania](../build/inference-rules.md)