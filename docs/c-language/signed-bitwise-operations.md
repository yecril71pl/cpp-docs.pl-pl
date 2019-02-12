---
title: Operacje bitowe ze znakiem
ms.date: 11/04/2016
helpviewer_keywords:
- bitwise operations
- signed bitwise operations
ms.assetid: 1e5cf65b-ee32-41a0-a5c2-82c1854091f6
ms.openlocfilehash: 43f65fd5d1ea14ef5e15f18d9c8516ccf5fb1e08
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2019
ms.locfileid: "56147597"
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

## <a name="see-also"></a>Zobacz także

[Liczby całkowite](../c-language/integers.md)
