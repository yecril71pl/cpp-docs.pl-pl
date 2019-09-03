---
title: __emul, __emulu
ms.date: 09/02/2019
f1_keywords:
- __emulu_cpp
- __emul
- __emul_cpp
- __emulu
helpviewer_keywords:
- __emul intrinsic
- __emulu intrinsic
ms.assetid: 79545236-cca2-40b8-a4e1-8abce9b26311
ms.openlocfilehash: 16b2b38f6f44b99c9f5b9370ba586342a860684e
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216745"
---
# <a name="__emul-__emulu"></a>__emul, __emulu

**Microsoft Specific**

Wykonuje operacje mnożenia, które przepełnią wartość 32-bitową liczbę całkowitą.

## <a name="syntax"></a>Składnia

```C
__int64 __emul(
   int a,
   int b
);
unsigned __int64 __emulu(
   unsigned int a,
   unsigned int b
);
```

### <a name="parameters"></a>Parametry

*z*\
podczas Pierwszy operand liczby całkowitej mnożenia.

*b*\
podczas Drugi operand liczby całkowitej mnożenia.

## <a name="return-value"></a>Wartość zwracana

Wynik mnożenia.

## <a name="requirements"></a>Wymagania

|Wewnętrznej|Architektura|
|---------------|------------------|
|`__emul`|x86, x64|
|`__emulu`|x86, x64|

**Plik nagłówka** \<intrin. h >

## <a name="remarks"></a>Uwagi

`__emul`Pobiera 2 32-bitowe wartości podpisane i zwraca wynik mnożenia jako 64-bitową liczbę całkowitą ze znakiem.

`__emulu`Pobiera 2 32-bitową liczbę całkowitą bez znaku i zwraca wynik mnożenia jako 64-bitową liczbę całkowitą bez znaku.

## <a name="example"></a>Przykład

```cpp
// emul.cpp
// compile with: /EHsc
// processor: x86, x64
#include <iostream>
#include <intrin.h>
using namespace std;

#pragma intrinsic(__emul)
#pragma intrinsic(__emulu)

int main()
{
   int a = -268435456;
   int b = 2;

   __int64 result = __emul(a, b);

   cout << a << " * " << b << " = " << result << endl;

   unsigned int ua = 0xFFFFFFFF; // Dec value: 4294967295
   unsigned int ub = 0xF000000;  // Dec value: 251658240

   unsigned __int64 uresult = __emulu(ua, ub);

   cout << ua << " * " << ub << " = " << uresult << endl;

}
```

## <a name="output"></a>Dane wyjściowe

```Output
-268435456 * 2 = -536870912
4294967295 * 251658240 = 1080863910317260800
```

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)
