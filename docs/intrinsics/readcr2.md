---
title: __readcr2
ms.date: 09/02/2019
f1_keywords:
- __readcr2
helpviewer_keywords:
- __readcr2 intrinsic
ms.assetid: d02c97d8-1953-46e7-a79e-a781e2c5bf27
ms.openlocfilehash: 482f4548a692d6aa3b65fbc42caabda29bb393c1
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217104"
---
# <a name="__readcr2"></a>__readcr2

**Microsoft Specific**

Odczytuje rejestr CR2 i zwraca jego wartość.

## <a name="syntax"></a>Składnia

```C
unsigned __int64 __readcr2(void);
```

## <a name="return-value"></a>Wartość zwracana

Wartość w rejestrze CR2.

## <a name="requirements"></a>Wymagania

|Wewnętrznej|Architektura|
|---------------|------------------|
|`__readcr2`|x86, x64|

**Plik nagłówka** \<intrin. h >

## <a name="remarks"></a>Uwagi

Element wewnętrzny jest dostępny tylko w trybie jądra, a procedura jest dostępna tylko jako wewnętrzna.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)
