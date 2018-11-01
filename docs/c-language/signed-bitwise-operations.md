---
title: Operacje bitowe ze znakiem
ms.date: 11/04/2016
helpviewer_keywords:
- bitwise operations
- signed bitwise operations
ms.assetid: 1e5cf65b-ee32-41a0-a5c2-82c1854091f6
ms.openlocfilehash: d178900a25a5d7a080068fb1919fcba2853bef14
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50652013"
---
# <a name="signed-bitwise-operations"></a>Operacje bitowe ze znakiem

**ANSI 3.3** wyniki Operacje bitowe na liczby całkowite ze znakiem

Operacje bitowe na liczby całkowite ze znakiem działać tak samo, jak operacje bitowe na liczb całkowitych bez znaku. Na przykład `-16 & 99` mogą być wyrażone w danych binarnych jako

```
  11111111 11110000
& 00000000 01100011
  _________________
  00000000 01100000
```

Bitowe AND powstaje 96.

## <a name="see-also"></a>Zobacz też

[Liczby całkowite](../c-language/integers.md)