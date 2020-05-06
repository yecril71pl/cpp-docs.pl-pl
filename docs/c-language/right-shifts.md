---
title: Przesunięcia w prawo
ms.date: 11/04/2016
ms.assetid: c878e97d-ea3c-4c6b-90a8-b1b24b2d5b19
ms.openlocfilehash: c34373f69a41ad65031753cd352098dce7e98ef4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62158362"
---
# <a name="right-shifts"></a>Przesunięcia w prawo

Wynik prawej zmiany typu całkowitego ze znakiem z wartością ujemną

Przesunięcie wartości ujemnej na prawo daje połowę wartość bezwzględną, zaokrągloną w dół. Na przykład podpisana `short` wartość-253 (szesnastkowa 0xFF03, binarne 11111111 00000011) przesunięta w prawo o jeden bit produkuje-127 (szesnastkowo 0xFF81, Binary 11111111 10000001). Dodatnie przesunięcie w prawo 253 produkuje + 126.

Prawy Shift zachowuje bit znaku podpisanych typów całkowitych. Gdy liczba całkowita ze znakiem zostanie przesunięta w prawo, to najbardziej znaczący bit pozostaje ustawiony. Na przykład jeśli 0xF0000000 jest podpisany `int`, przesunięcie w prawo powoduje 0xF8000000. Przesunięcie negatywnego `int` prawa 32 razy tworzy 0xFFFFFFFF.

Gdy liczba całkowita bez znaku zostaje przesunięta w prawo, najbardziej znaczący bit jest wyczyszczony. Na przykład jeśli 0xF000 jest niepodpisana, wynikiem jest 0x7800. Przesunięcie `unsigned` lub dodatnie `int` prawo 32 razy produkuje.

## <a name="see-also"></a>Zobacz też

[Liczby całkowite](../c-language/integers.md)
