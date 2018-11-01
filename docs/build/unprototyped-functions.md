---
title: Funkcje bez pierwowzoru
ms.date: 11/04/2016
ms.assetid: 34200b8c-5b52-4f0d-aff8-9f70d82868ed
ms.openlocfilehash: 38207be6111dadc338593e55b683b88e0480e1ca
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50633431"
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