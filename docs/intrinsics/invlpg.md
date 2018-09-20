---
title: __invlpg | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __invlpg
- __invlpg_cpp
dev_langs:
- C++
helpviewer_keywords:
- invlpg instruction
- __invlpg intrinsic
ms.assetid: 3fb3633f-d9b7-4ec0-9e7f-a7f2fa8ed794
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 01a35d110c56bba6b89c5bf34dedec61bde90794
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46403217"
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

## <a name="see-also"></a>Zobacz też

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)