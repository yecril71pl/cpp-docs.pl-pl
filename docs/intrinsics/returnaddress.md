---
title: _ReturnAddress
ms.date: 11/04/2016
f1_keywords:
- _ReturnAddress
helpviewer_keywords:
- _ReturnAddress intrinsic
- ReturnAddress intrinsic
ms.assetid: 7f4a5811-35e6-4f64-ba7c-21203380eeda
ms.openlocfilehash: e5013b20f9e7ed0349d940d9be61cc1b4afc95d4
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59041140"
---
# <a name="returnaddress"></a>_ReturnAddress

## <a name="microsoft-specific"></a>Specyficzne dla firmy Microsoft

`_ReturnAddress` Wewnętrzne udostępnia adres instrukcji w funkcji wywołującej, która zostanie wykonana po sterowanie powraca do obiektu wywołującego.

Twórz następujący program i wykonywania krokowego w debugerze. Podczas wykonywania kroków za pośrednictwem programu, należy pamiętać, adres, który jest zwracany z `_ReturnAddress`. Następnie natychmiast po powrocie z tej funkcji gdzie `_ReturnAddress` była używana, otwórz [jak: Korzystanie z okna dezasemblacji](/visualstudio/debugger/how-to-use-the-disassembly-window) i zwróć uwagę, że adres następnej instrukcji do wykonania odpowiada adres, który został zwrócony z `_ReturnAddress`.

Optymalizacje, takie jak wbudowanie może mieć wpływ na adres zwrotny. Na przykład, jeśli poniższy przykładowy program został skompilowany z [/Ob1](../build/reference/ob-inline-function-expansion.md), `inline_func` jest wbudowana w funkcji wywołującej `main`. W związku z tym, wywołania `_ReturnAddress` z `inline_func` i `main` będzie każde produkuje taką samą wartość.

Gdy `_ReturnAddress` jest używany w programie skompilowany przy użyciu [/CLR](../build/reference/clr-common-language-runtime-compilation.md), zawierający funkcję `_ReturnAddress` wywołanie zostanie skompilowany w macierzystym funkcji. Gdy funkcja skompilowana jako zarządzana wywołania do funkcji zawierający `_ReturnAddress`, `_ReturnAddress` może nie działać zgodnie z oczekiwaniami.

## <a name="requirements"></a>Wymagania

**Plik nagłówkowy** \<intrin.h >

## <a name="example"></a>Przykład

```
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

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[_AddressOfReturnAddress](../intrinsics/addressofreturnaddress.md)<br/>
[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)