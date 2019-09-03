---
title: __readcr0
ms.date: 09/02/2019
f1_keywords:
- __readcr0
helpviewer_keywords:
- __readcr0 intrinsic
ms.assetid: 25bdb093-d83c-48d7-9c0f-224de8e2c61c
ms.openlocfilehash: 8f3abc7177fa2e648c02eab498d04bcada96bb06
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70221283"
---
# <a name="__readcr0"></a>__readcr0

**Microsoft Specific**

Odczytuje rejestr CR0 i zwraca jego wartość.

## <a name="syntax"></a>Składnia

```C
unsigned long __readcr0(void);  /* X86 */
unsigned __int64 __readcr0(void);  /* X64 */
```

## <a name="return-value"></a>Wartość zwracana

Wartość w rejestrze CR0.

## <a name="requirements"></a>Wymagania

|Wewnętrznej|Architektura|
|---------------|------------------|
|`__readcr0`|x86, x64|

**Plik nagłówka** \<intrin. h >

## <a name="remarks"></a>Uwagi

Element wewnętrzny jest dostępny tylko w trybie jądra, a procedura jest dostępna tylko jako wewnętrzna.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)
