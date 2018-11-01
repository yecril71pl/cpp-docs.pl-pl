---
title: _AddressOfReturnAddress
ms.date: 11/04/2016
f1_keywords:
- _AddressOfReturnAddress_cpp
- _AddressOfReturnAddress
helpviewer_keywords:
- _AddressOfReturnAddress intrinsic
- AddressOfReturnAddress intrinsic
ms.assetid: c7e10b8c-445e-4236-a602-e2d90200f70a
ms.openlocfilehash: 678128c4b09b083b4afe3a86c9b2315eb3c87b1b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50584486"
---
# <a name="addressofreturnaddress"></a>_AddressOfReturnAddress

**Microsoft Specific**

Udostępnia adres lokalizacji w pamięci, który zawiera adres zwrotny bieżącą funkcję. Ten adres nie może być umożliwia dostęp do innych lokalizacji pamięci (na przykład argumenty funkcji).

## <a name="syntax"></a>Składnia

```
void * _AddressOfReturnAddress();
```

## <a name="requirements"></a>Wymagania

|Wewnętrzne|Architektura|
|---------------|------------------|
|`_AddressOfReturnAddress`|x86, x64|

**Plik nagłówkowy** \<intrin.h >

## <a name="remarks"></a>Uwagi

Gdy `_AddressOfReturnAddress` jest używany w programie skompilowany przy użyciu [/CLR](../build/reference/clr-common-language-runtime-compilation.md), zawierający funkcję `_AddressOfReturnAddress` wywołanie jest skompilowany w macierzystym funkcji. Gdy funkcja skompilowana jako zarządzana wywołania do funkcji zawierający `_AddressOfReturnAddress`, `_AddressOfReturnAddress` może nie działać zgodnie z oczekiwaniami.

Ta procedura jest dostępna wyłącznie jako wewnętrzna.

## <a name="example"></a>Przykład

```
// compiler_intrinsics_AddressOfReturnAddress.cpp
// processor: x86, x64
#include <stdio.h>
#include <intrin.h>

// This function will print three values:
//   (1) The address retrieved from _AddressOfReturnAdress
//   (2) The return address stored at the location returned in (1)
//   (3) The return address retrieved the _ReturnAddress* intrinsic
// Note that (2) and (3) should be the same address.
__declspec(noinline)
void func() {
   void* pvAddressOfReturnAddress = _AddressOfReturnAddress();
   printf_s("%p\n", pvAddressOfReturnAddress);
   printf_s("%p\n", *((void**) pvAddressOfReturnAddress));
   printf_s("%p\n", _ReturnAddress());
}

int main() {
   func();
}
```

```Output
0012FF78
00401058
00401058
```

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz też

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)