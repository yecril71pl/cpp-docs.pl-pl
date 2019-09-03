---
title: _ReturnAddress
ms.date: 09/02/2019
f1_keywords:
- _ReturnAddress
helpviewer_keywords:
- _ReturnAddress intrinsic
- ReturnAddress intrinsic
ms.assetid: 7f4a5811-35e6-4f64-ba7c-21203380eeda
ms.openlocfilehash: 2a830ff1e8a2c9551dec52cf10a3d5cf126bde3b
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218058"
---
# <a name="_returnaddress"></a>_ReturnAddress

**Microsoft Specific**

`_ReturnAddress` Wewnętrzna udostępnia adres instrukcji w funkcji wywołującej, która zostanie wykonana po powrocie kontroli do obiektu wywołującego.

Skompiluj następujący program i przejdź do niego w debugerze. Po przekroczeniu tego programu należy zwrócić uwagę na adres zwrócony przez `_ReturnAddress`. Następnie natychmiast po powrocie z funkcji, w `_ReturnAddress` której został użyty, [Otwórz instrukcje: Użyj okna](/visualstudio/debugger/how-to-use-the-disassembly-window) demontaż i zwróć uwagę, że adres następnej instrukcji do wykonania jest zgodny z adresem zwróconym z `_ReturnAddress`.

Optymalizacje, takie jak tworzenie konspektu, mogą mieć wpływ na adres zwrotny. Jeśli na przykład Przykładowy program został skompilowany z [/OB1](../build/reference/ob-inline-function-expansion.md), `inline_func` zostanie wbudowany w funkcję `main`wywołującą. W związku z tym wywołania `_ReturnAddress` z `inline_func` i `main` będą miały taką samą wartość.

Gdy `_ReturnAddress` jest używany w programie skompilowanym z [/CLR](../build/reference/clr-common-language-runtime-compilation.md), funkcja zawierająca `_ReturnAddress` wywołanie zostanie skompilowana jako funkcja natywna. Gdy funkcja skompilowana jako wywołania zarządzane do funkcji zawierającej `_ReturnAddress`, `_ReturnAddress` może nie zachowywać się zgodnie z oczekiwaniami.

## <a name="requirements"></a>Wymagania

**Plik nagłówka** \<intrin. h >

## <a name="example"></a>Przykład

```cpp
// compiler_intrinsics__ReturnAddress.cpp
#include <stdio.h>
#include <intrin.h>

#pragma intrinsic(_ReturnAddress)

__declspec(noinline)
void noinline_func(void)
{
   printf("Return address from %s: %p\n", __FUNCTION__, _ReturnAddress());
}

__forceinline
void inline_func(void)
{
   printf("Return address from %s: %p\n", __FUNCTION__, _ReturnAddress());
}

int main(void)
{
   noinline_func();
   inline_func();
   printf("Return address from %s: %p\n", __FUNCTION__, _ReturnAddress());

   return 0;
}
```

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[_AddressOfReturnAddress](../intrinsics/addressofreturnaddress.md)\
[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)\
[Słowa kluczowe](../cpp/keywords-cpp.md)
