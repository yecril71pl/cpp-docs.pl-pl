---
title: __indword
ms.date: 09/02/2019
f1_keywords:
- __indword_cpp
- __indword
helpviewer_keywords:
- in instruction
- __indword intrinsic
ms.assetid: 1068d686-586e-4e36-b962-d1d7c3315260
ms.openlocfilehash: 790b65c8a565124df92b82b7ea17174788086a96
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222116"
---
# <a name="__indword"></a>__indword

**Microsoft Specific**

Odczytuje jedno podwójne słowo danych z określonego portu przy użyciu `in` instrukcji.

## <a name="syntax"></a>Składnia

```C
unsigned long __indword(
   unsigned short Port
);
```

### <a name="parameters"></a>Parametry

*Przewożąc*\
podczas Port, z którego ma zostać odczytany.

## <a name="return-value"></a>Wartość zwracana

Wyraz odczytany z portu.

## <a name="requirements"></a>Wymagania

|Wewnętrznej|Architektura|
|---------------|------------------|
|`__indword`|x86, x64|

**Plik nagłówka** \<intrin. h >

## <a name="remarks"></a>Uwagi

Ta procedura jest dostępna tylko jako wewnętrzna.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)
