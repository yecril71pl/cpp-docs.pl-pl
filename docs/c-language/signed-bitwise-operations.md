---
title: Operacje bitowe ze znakiem
ms.date: 11/04/2016
helpviewer_keywords:
- bitwise operations
- signed bitwise operations
ms.assetid: 1e5cf65b-ee32-41a0-a5c2-82c1854091f6
ms.openlocfilehash: 43f65fd5d1ea14ef5e15f18d9c8516ccf5fb1e08
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62158322"
---
# <a name="signed-bitwise-operations"></a>Operacje bitowe ze znakiem

**ANSI 3,3** Wyniki operacji bitowych w przypadku liczb całkowitych ze znakiem

Operacje bitowe w podpisanych liczbach całkowitych działają tak samo jak operacje bitowe w liczbach całkowitych bez znaku. Na przykład `-16 & 99` może być wyrażona jako plik binarny jako

```
  11111111 11110000
& 00000000 01100011
  _________________
  00000000 01100000
```

Wynik bitowy jest 96.

## <a name="see-also"></a>Zobacz też

[Liczby całkowite](../c-language/integers.md)
