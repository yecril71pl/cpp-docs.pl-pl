---
title: __invlpg
ms.date: 11/04/2016
f1_keywords:
- __invlpg
- __invlpg_cpp
helpviewer_keywords:
- invlpg instruction
- __invlpg intrinsic
ms.assetid: 3fb3633f-d9b7-4ec0-9e7f-a7f2fa8ed794
ms.openlocfilehash: b4f941baae9f03ed288a99d59e2b06262962e339
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62348747"
---
# <a name="invlpg"></a>__invlpg

**Microsoft Specific**

Generuje x86 `invlpg` instrukcji, co unieważnia buforu referencyjnych tłumaczenia (TLB) dla strony skojarzone z pamięci wskazywany przez `Address`.

## <a name="syntax"></a>Składnia

```
void __invlpg(
   void* Address
);
```

#### <a name="parameters"></a>Parametry

*Adres*<br/>
[in] 64-bitowy adres.

## <a name="requirements"></a>Wymagania

|Wewnętrzne|Architektura|
|---------------|------------------|
|`__invlpg`|x86, x64|

**Plik nagłówkowy** \<intrin.h >

## <a name="remarks"></a>Uwagi

Wewnętrzne `__invlpg` emituje instrukcja uprzywilejowana i jest dostępna tylko w trybie jądra z poziomem uprawnień (Panel sterowania) 0.

Ta procedura jest dostępna wyłącznie jako wewnętrzna.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)