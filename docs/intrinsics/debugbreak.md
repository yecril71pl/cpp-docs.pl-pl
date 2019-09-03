---
title: __debugbreak
ms.date: 09/02/2019
f1_keywords:
- __debugbreak_cpp
- __debugbreak
helpviewer_keywords:
- breakpoints, __debugbreak intrinsic
- __debugbreak intrinsic
ms.assetid: 1d1e1c0c-891a-4613-ae4b-d790094ba830
ms.openlocfilehash: e4cf2c85818a878417c560ddb5a80f8690e60a93
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217925"
---
# <a name="__debugbreak"></a>__debugbreak

**Microsoft Specific**

Powoduje, że punkt przerwania w kodzie, w którym użytkownik zostanie poproszony o uruchomienie debugera.

## <a name="syntax"></a>Składnia

```C
void __debugbreak();
```

## <a name="requirements"></a>Wymagania

|Wewnętrznej|Architektura|nagłówek|
|---------------|------------------|------------|
|`__debugbreak`|x86, x64, ARM, ARM64|\<intrin.h>|

## <a name="remarks"></a>Uwagi

Wewnętrzny kompilator, podobny do DebugBreak, jest przenośnym sposobem na działanie punktu przerwania. [](/windows/win32/api/debugapi/nf-debugapi-debugbreak) `__debugbreak`

> [!NOTE]
> Podczas kompilowania z **/CLR**, funkcja zawierająca `__debugbreak` zostanie skompilowana do MSIL. `asm int 3`powoduje, że funkcja jest skompilowana do kodu natywnego. Aby uzyskać więcej informacji, zobacz [__asm](../assembler/inline/asm.md).

Przykład:

```C
main() {
   __debugbreak();
}
```

jest podobny do:

```C
main() {
   __asm {
      int 3
   }
}
```

na komputerze z procesorem x86.

W programie arm64 `__debugbreak` wewnętrznie jest kompilowane do instrukcji `brk #0xF000`.

Ta procedura jest dostępna tylko jako wewnętrzna.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)\
[Słowa kluczowe](../cpp/keywords-cpp.md)
