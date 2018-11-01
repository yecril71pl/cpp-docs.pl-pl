---
title: __debugbreak
ms.date: 11/04/2016
f1_keywords:
- __debugbreak_cpp
- __debugbreak
helpviewer_keywords:
- breakpoints, __debugbreak intrinsic
- __debugbreak intrinsic
ms.assetid: 1d1e1c0c-891a-4613-ae4b-d790094ba830
ms.openlocfilehash: 72fe358f379656a05d840246c4d525bbabc9e9e8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50591106"
---
# <a name="debugbreak"></a>__debugbreak

**Microsoft Specific**

Powoduje, że punkt przerwania w kodzie, gdzie użytkownik jest monitowany o uruchomienia debugera.

## <a name="syntax"></a>Składnia

```
void __debugbreak();
```

## <a name="requirements"></a>Wymagania

|Wewnętrzne|Architektura|nagłówek|
|---------------|------------------|------------|
|`__debugbreak`|x86, ARM, x64|\<intrin.h>|

## <a name="remarks"></a>Uwagi

`__debugbreak` Kompilatora wewnętrzne, podobnie jak [DebugBreak](https://msdn.microsoft.com/library/windows/desktop/ms679297.aspx), jest przenośny sposób Win32 i spowodować, że punkt przerwania.

> [!NOTE]
>  Podczas kompilowania za pomocą **/CLR**, funkcja nadrzędnym `__debugbreak` zostaną skompilowane do MSIL. `asm int 3` powoduje, że funkcja jest kompilowana do natywnego. Aby uzyskać więcej informacji, zobacz [__asm](../assembler/inline/asm.md).

Na przykład:

```
main() {
   __debugbreak();
}
```

jest podobny do:

```
main() {
   __asm {
      int 3
   }
}
```

na x86 komputera.

Ta procedura jest dostępna wyłącznie jako wewnętrzna.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz też

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)