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
ms.openlocfilehash: b52c34014402a235e03c45f82dcd1e5c542e4919
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59023103"
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

## <a name="see-also"></a>Zobacz także

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)