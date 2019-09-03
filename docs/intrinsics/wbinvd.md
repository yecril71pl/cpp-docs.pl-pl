---
title: __wbinvd
ms.date: 09/02/2019
f1_keywords:
- __wbinvd
helpviewer_keywords:
- __wbinvd intrinsic
- wbinvd instruction
ms.assetid: 628d0981-39e5-49e1-bd43-706d123af121
ms.openlocfilehash: fe888ef578f0c2e077911537d401890b63372a0b
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219386"
---
# <a name="__wbinvd"></a>__wbinvd

**Microsoft Specific**

Generuje instrukcję Write-back i unvalidate cache`wbinvd`().

## <a name="syntax"></a>Składnia

```C
void __wbinvd(void);
```

## <a name="requirements"></a>Wymagania

|Wewnętrznej|Architektura|
|---------------|------------------|
|`__wbinvd`|x86, x64|

**Plik nagłówka** \<intrin. h >

## <a name="remarks"></a>Uwagi

Ta funkcja jest dostępna tylko w trybie jądra z poziomem uprawnień (CPL) o wartości 0, a procedura jest dostępna tylko jako wewnętrzna.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)
