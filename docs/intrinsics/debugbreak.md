---
title: __debugbreak | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __debugbreak_cpp
- __debugbreak
dev_langs:
- C++
helpviewer_keywords:
- breakpoints, __debugbreak intrinsic
- __debugbreak intrinsic
ms.assetid: 1d1e1c0c-891a-4613-ae4b-d790094ba830
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f2ba9322f4fe94c1c857b0494dc79b417e5d65d8
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46433901"
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