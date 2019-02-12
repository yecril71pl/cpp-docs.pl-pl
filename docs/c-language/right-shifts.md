---
title: Przesunięcia w prawo
ms.date: 11/04/2016
ms.assetid: c878e97d-ea3c-4c6b-90a8-b1b24b2d5b19
ms.openlocfilehash: c34373f69a41ad65031753cd352098dce7e98ef4
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2019
ms.locfileid: "56149482"
---
# <a name="right-shifts"></a>Przesunięcia w prawo

Typ całkowitoliczbowy ze znakiem wynik przesunięcia w prawo wartość ujemna

Przesunięcie wartości ujemnej po prawej stronie daje połowa wartość bezwzględną, zaokrąglona w dół. Na przykład podpisane `short` wartość -253 (0xFF03 szesnastkowych, binarne 00000011 11111111) przesunięte w prawo o jeden bit generuje -127 (0xFF81 szesnastkowych, binarne 10000001 11111111). Dodatnią 253 przesunięte w prawo generuje +126.

Przesunięcia w prawo zachować bitu znaku podpisanych typów całkowitych. Liczba całkowita ze znakiem przenosi bezpośrednio, ustaw pozostaje najbardziej znaczący bit. Na przykład, jeśli 0xF0000000 jest podpisana `int`, przesunięcia bitowego w prawo powoduje 0xF8000000. Przesunięcie ujemnych `int` bezpośrednio 32 godziny tworzy 0xFFFFFFFF.

Gdy liczbą całkowitą bez znaku przenosi bezpośrednio, najbardziej znaczący bit jest wyczyszczone. Na przykład jeśli 0xF000 jest podpisany, wynik jest 0x7800. Przesunięcie `unsigned` lub być liczbami dodatnimi `int` bezpośrednio 32 godziny tworzy 0x00000000.

## <a name="see-also"></a>Zobacz także

[Liczby całkowite](../c-language/integers.md)
