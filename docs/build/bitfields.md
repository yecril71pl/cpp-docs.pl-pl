---
title: Pola bitów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- bitfields
ms.assetid: e9a1010d-1e1b-487f-9943-3c574e08f544
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a7451ea6afee81cc296fb091705bde48041ef5d1
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45722491"
---
# <a name="bitfields"></a>Pola bitów

Struktura pola bitowe są ograniczone do 64-bitowy i może być typu podpisany int, niepodpisane int, int64 lub int64 bez znaku. Pola bitowe, które przecinają granice typu pominie bitów, aby wyrównać bitfield do następnego wyrównanie typu. Na przykład pola bitów liczba całkowita, nie mogą przekroczyć graniczny 32-bitowych.

## <a name="see-also"></a>Zobacz też

[Typy i magazyn](../build/types-and-storage.md)