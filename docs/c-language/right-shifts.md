---
title: Kliknij prawym przyciskiem myszy przesunięcia | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: c878e97d-ea3c-4c6b-90a8-b1b24b2d5b19
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f31ebddb38d1eb1cafe9495f8c121811ec502524
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46032421"
---
# <a name="right-shifts"></a>Przesunięcia w prawo

Typ całkowitoliczbowy ze znakiem wynik przesunięcia w prawo wartość ujemna

Przesunięcie wartości ujemnej po prawej stronie daje połowa wartość bezwzględną, zaokrąglona w dół. Na przykład podpisane `short` wartość -253 (0xFF03 szesnastkowych, binarne 00000011 11111111) przesunięte w prawo o jeden bit generuje -127 (0xFF81 szesnastkowych, binarne 10000001 11111111). Dodatnią 253 przesunięte w prawo generuje +126.

Przesunięcia w prawo zachować bitu znaku podpisanych typów całkowitych. Liczba całkowita ze znakiem przenosi bezpośrednio, ustaw pozostaje najbardziej znaczący bit. Na przykład, jeśli 0xF0000000 jest podpisana `int`, przesunięcia bitowego w prawo powoduje 0xF8000000. Przesunięcie ujemnych `int` bezpośrednio 32 godziny tworzy 0xFFFFFFFF.

Gdy liczbą całkowitą bez znaku przenosi bezpośrednio, najbardziej znaczący bit jest wyczyszczone. Na przykład jeśli 0xF000 jest podpisany, wynik jest 0x7800. Przesunięcie `unsigned` lub być liczbami dodatnimi `int` bezpośrednio 32 godziny tworzy 0x00000000.

## <a name="see-also"></a>Zobacz też

[Liczby całkowite](../c-language/integers.md)