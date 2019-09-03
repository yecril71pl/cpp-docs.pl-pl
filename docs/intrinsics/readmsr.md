---
title: __readmsr
ms.date: 09/02/2019
f1_keywords:
- __readmsr
helpviewer_keywords:
- Read Model Specific Register
- rdmsr instruction
- __readmsr intrinsic
ms.assetid: 7ab1f8e8-72cb-4ce4-817d-3e728a3c9716
ms.openlocfilehash: 4398b9d42369e3a914dbec1ed2d14cafecf58483
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222342"
---
# <a name="__readmsr"></a>__readmsr

**Microsoft Specific**

Generuje instrukcję, która odczytuje rejestr specyficzny dla modelu określony przez `register` i zwraca jego wartość. `rdmsr`

## <a name="syntax"></a>Składnia

```C
__int64 __readmsr(
   int register
);
```

### <a name="parameters"></a>Parametry

*zarejestrować*\
podczas Rejestr specyficzny dla modelu, który ma zostać odczytany.

## <a name="return-value"></a>Wartość zwracana

Wartość w określonym rejestrze.

## <a name="requirements"></a>Wymagania

|Wewnętrznej|Architektura|
|---------------|------------------|
|`__readmsr`|x86, x64|

**Plik nagłówka** \<intrin. h >

## <a name="remarks"></a>Uwagi

Ta funkcja jest dostępna tylko w trybie jądra, a procedura jest dostępna tylko jako wewnętrzna.

Aby uzyskać więcej informacji, zobacz dokumentację AMD.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)
