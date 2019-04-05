---
title: __ud2
ms.date: 11/04/2016
f1_keywords:
- __ud2
helpviewer_keywords:
- UD2 instruction
- __ud2 intrinsic
ms.assetid: 0831cd5a-8b65-402e-bb57-11e1d5d7ffd2
ms.openlocfilehash: a36ab5c25ac9138b2a4d6810cc2a339e534f1695
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "59029411"
---
# <a name="ud2"></a>__ud2

**Specyficzne dla firmy Microsoft**

Generuje instrukcję niezdefiniowane.

## <a name="syntax"></a>Składnia

```
void __ud2();
```

## <a name="remarks"></a>Uwagi

Procesor zgłasza wyjątek nieprawidłowy kod operacji, jeśli zostanie wykonana instrukcja niezdefiniowane.

`__ud2` Funkcji jest odpowiednikiem `UD2` komputera instrukcji i jest dostępna tylko w trybie jądra. Aby uzyskać więcej informacji, wyszukaj dokumentu, "Manual deweloper oprogramowania architekturze firmy Intel, wolumin 2: Instrukcja Ustaw odwołanie,"w [Intel Corporation](https://software.intel.com/articles/intel-sdm) lokacji.

## <a name="requirements"></a>Wymagania

|Wewnętrzne|Architektura|
|---------------|------------------|
|`__ud2`|x86, x64|

**Plik nagłówkowy** \<intrin.h >

**KONIEC Specyficzne dla firmy Microsoft**

## <a name="example"></a>Przykład

Poniższy przykład wykonuje instrukcja niezdefiniowane zgłasza wyjątek. Obsługa wyjątków następnie zmienia kod powrotny od zera do jednego.

```
// __ud2_intrinsic.cpp
#include <stdio.h>
#include <intrin.h>
#include <excpt.h>
// compile with /EHa

int main() {

// Initialize the return code to 0.
int ret = 0;

// Attempt to execute an undefined instruction.
  printf("Before __ud2(). Return code = %d.\n", ret);
  __try {
  __ud2();
  }

// Catch any exceptions and set the return code to 1.
  __except(EXCEPTION_EXECUTE_HANDLER){
  printf("  In the exception handler.\n");
  ret = 1;
  }

// Report the value of the return code.
  printf("After __ud2().  Return code = %d.\n", ret);
  return ret;
}
```

```Output
Before __ud2(). Return code = 0.
  In the exception handler.
After __ud2().  Return code = 1.
```

## <a name="see-also"></a>Zobacz także

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)