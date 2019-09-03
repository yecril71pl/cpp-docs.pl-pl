---
title: _AddressOfReturnAddress
ms.date: 09/02/2019
f1_keywords:
- _AddressOfReturnAddress_cpp
- _AddressOfReturnAddress
helpviewer_keywords:
- _AddressOfReturnAddress intrinsic
- AddressOfReturnAddress intrinsic
ms.assetid: c7e10b8c-445e-4236-a602-e2d90200f70a
ms.openlocfilehash: d705029c30fdbc117c4c6e96923691e43e072e23
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70221074"
---
# <a name="_addressofreturnaddress"></a>_AddressOfReturnAddress

**Microsoft Specific**

Udostępnia adres lokalizacji pamięci, która przechowuje adres zwrotny bieżącej funkcji. Tego adresu nie można używać do uzyskiwania dostępu do innych lokalizacji pamięci (na przykład argumentów funkcji).

## <a name="syntax"></a>Składnia

```C
void * _AddressOfReturnAddress();
```

## <a name="requirements"></a>Wymagania

|Wewnętrznej|Architektura|
|---------------|------------------|
|`_AddressOfReturnAddress`|x86, x64, ARM, ARM64|

**Plik nagłówka** \<intrin. h >

## <a name="remarks"></a>Uwagi

Gdy `_AddressOfReturnAddress` jest używany w programie skompilowanym z [/CLR](../build/reference/clr-common-language-runtime-compilation.md), funkcja zawierająca `_AddressOfReturnAddress` wywołanie jest kompilowana jako funkcja natywna. Gdy funkcja skompilowana jako wywołania zarządzane do funkcji zawierającej `_AddressOfReturnAddress`, `_AddressOfReturnAddress` może nie zachowywać się zgodnie z oczekiwaniami.

Ta procedura jest dostępna tylko jako wewnętrzna.

## <a name="example"></a>Przykład

```cpp
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

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)\
[Słowa kluczowe](../cpp/keywords-cpp.md)
