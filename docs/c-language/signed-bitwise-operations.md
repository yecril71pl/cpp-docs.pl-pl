---
title: Operacje bitowe ze znakiem | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- bitwise operations
- signed bitwise operations
ms.assetid: 1e5cf65b-ee32-41a0-a5c2-82c1854091f6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 184fd5a0e6c12cb58e9fed759459e7b8172896f8
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46038300"
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