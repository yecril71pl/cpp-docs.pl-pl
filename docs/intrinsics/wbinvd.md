---
title: __wbinvd
ms.date: 11/04/2016
f1_keywords:
- __wbinvd
helpviewer_keywords:
- __wbinvd intrinsic
- wbinvd instruction
ms.assetid: 628d0981-39e5-49e1-bd43-706d123af121
ms.openlocfilehash: 0f775ba94c2dee1c2568e66b09fa1ffb31f512bb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50482540"
---
# <a name="wbinvd"></a>__wbinvd

**Microsoft Specific**

Generuje zapisuj zwrotnie i unieważnienia pamięci podręcznej (`wbinvd`) instrukcji.

## <a name="syntax"></a>Składnia

```
void __wbinvd(void);
```

## <a name="requirements"></a>Wymagania

|Wewnętrzne|Architektura|
|---------------|------------------|
|`__wbinvd`|x86, x64|

**Plik nagłówkowy** \<intrin.h >

## <a name="remarks"></a>Uwagi

Ta funkcja jest dostępna tylko w trybie jądra z poziomem uprawnień (Panel sterowania), 0, a procedura jest dostępna jako funkcja wewnętrzna tylko.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz też

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)