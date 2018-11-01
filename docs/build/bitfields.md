---
title: Pola bitów
ms.date: 11/04/2016
helpviewer_keywords:
- bitfields
ms.assetid: e9a1010d-1e1b-487f-9943-3c574e08f544
ms.openlocfilehash: 3ff0092bbd31b8b1cd98fa56fb802c7ce28cb472
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50652832"
---
# <a name="bitfields"></a>Pola bitów

Struktura pola bitowe są ograniczone do 64-bitowy i może być typu podpisany int, niepodpisane int, int64 lub int64 bez znaku. Pola bitowe, które przecinają granice typu pominie bitów, aby wyrównać bitfield do następnego wyrównanie typu. Na przykład pola bitów liczba całkowita, nie mogą przekroczyć graniczny 32-bitowych.

## <a name="see-also"></a>Zobacz też

[Typy i magazyn](../build/types-and-storage.md)