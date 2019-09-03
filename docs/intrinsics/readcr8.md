---
title: __readcr8
ms.date: 09/02/2019
f1_keywords:
- __readcr8
helpviewer_keywords:
- __readcr8 intrinsic
ms.assetid: fce16953-87ff-4fbe-8081-7962b97ae46c
ms.openlocfilehash: 525775fde4cb96cecfcabef878780d5a2aa6743a
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70221243"
---
# <a name="__readcr8"></a>__readcr8

**Microsoft Specific**

Odczytuje rejestr CR8 i zwraca jego wartość.

## <a name="syntax"></a>Składnia

```C
unsigned __int64 __readcr8(void);
```

## <a name="return-value"></a>Wartość zwracana

Wartość w rejestrze CR8.

## <a name="requirements"></a>Wymagania

|Wewnętrznej|Architektura|
|---------------|------------------|
|`__readcr8`|X64|

**Plik nagłówka** \<intrin. h >

## <a name="remarks"></a>Uwagi

Element wewnętrzny jest dostępny tylko w trybie jądra, a procedura jest dostępna tylko jako wewnętrzna.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)
