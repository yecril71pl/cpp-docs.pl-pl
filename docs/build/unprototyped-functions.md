---
title: Funkcje bez Pierwowzoru | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 34200b8c-5b52-4f0d-aff8-9f70d82868ed
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2c030bd99fc185b3c52535aecb45697672ef4c14
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45717681"
---
# <a name="unprototyped-functions"></a>Funkcje bez pierwowzoru

W przypadku funkcji nie jest w pełni prototypowane obiekt wywołujący przekazuje liczb całkowitych jako liczby całkowite i zmiennoprzecinkowe wartości jako podwójnej precyzji. Tylko wartości zmiennoprzecinkowych Zarejestruj liczba całkowita i zmiennoprzecinkowa rejestr będzie zawierać wartości zmiennoprzecinkowej w przypadku, gdy wywoływany oczekuje, że wartość w rejestrach liczby całkowitej.

```
func1();
func2() {   // RCX = 2, RDX = XMM1 = 1.0, and R8 = 7
   func1(2, 1.0, 7);
}
```

## <a name="see-also"></a>Zobacz też

[Konwencja wywoływania](../build/calling-convention.md)