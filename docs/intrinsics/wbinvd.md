---
title: __wbinvd
ms.date: 11/04/2016
f1_keywords:
- __wbinvd
helpviewer_keywords:
- __wbinvd intrinsic
- wbinvd instruction
ms.assetid: 628d0981-39e5-49e1-bd43-706d123af121
ms.openlocfilehash: 99c7a452e063dea328e4aa1362aae8783929deb0
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "59039270"
---
# <a name="wbinvd"></a>__wbinvd

**Specyficzne dla firmy Microsoft**

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

**KONIEC Specyficzne dla firmy Microsoft**

## <a name="see-also"></a>Zobacz także

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)