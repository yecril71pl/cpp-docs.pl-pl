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
ms.openlocfilehash: 029119bc47d0172c7e9cc5fbf8cd20c4ee23e0f0
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219654"
---
# <a name="__readmsr"></a>__readmsr

**Specyficzne dla firmy Microsoft**

Generuje `rdmsr` instrukcję, która odczytuje rejestr specyficzny dla modelu określony przez **`register`** i zwraca jego wartość.

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

**Plik nagłówka**\<intrin.h>

## <a name="remarks"></a>Uwagi

Ta funkcja jest dostępna tylko w trybie jądra, a procedura jest dostępna tylko jako wewnętrzna.

Aby uzyskać więcej informacji, zobacz dokumentację AMD.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)
