---
title: __ud2
ms.date: 09/02/2019
f1_keywords:
- __ud2
helpviewer_keywords:
- UD2 instruction
- __ud2 intrinsic
ms.assetid: 0831cd5a-8b65-402e-bb57-11e1d5d7ffd2
ms.openlocfilehash: b5aa20804099af4d75dcc62a5e62ccc0d4a09566
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219754"
---
# <a name="__ud2"></a>__ud2

**Microsoft Specific**

Generuje niezdefiniowaną instrukcję.

## <a name="syntax"></a>Składnia

```C
void __ud2();
```

## <a name="remarks"></a>Uwagi

Podczas wykonywania niezdefiniowanej instrukcji procesor zgłasza nieprawidłowy wyjątek kodu operacji.

Funkcja jest równoważna `UD2` z instrukcją Machine i jest dostępna tylko w trybie jądra. `__ud2` Aby uzyskać więcej informacji, Wyszukaj dokument "Podręcznik Intel Architecture Developer, Tom 2: Odwołanie do zestawu instrukcji "w witrynie [firmy Intel Corporation](https://software.intel.com/articles/intel-sdm) .

## <a name="requirements"></a>Wymagania

|Wewnętrznej|Architektura|
|---------------|------------------|
|`__ud2`|x86, x64|

**Plik nagłówka** \<intrin. h >

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="example"></a>Przykład

Poniższy przykład wykonuje niezdefiniowaną instrukcję, która wywołuje wyjątek. Program obsługi wyjątków zmieni Kod powrotu z zero na jeden.

```cpp
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
