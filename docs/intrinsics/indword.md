---
title: __indword
ms.date: 11/04/2016
f1_keywords:
- __indword_cpp
- __indword
helpviewer_keywords:
- in instruction
- __indword intrinsic
ms.assetid: 1068d686-586e-4e36-b962-d1d7c3315260
ms.openlocfilehash: f4b37247093da14c8d5e8fed69b01265d3fed2ee
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50599813"
---
# <a name="indword"></a>__indword

**Microsoft Specific**

Odczytuje jeden podwójne słowo danych z określonego portu przy użyciu `in` instrukcji.

## <a name="syntax"></a>Składnia

```
unsigned long __indword(
   unsigned short Port
);
```

#### <a name="parameters"></a>Parametry

*Port*<br/>
[in] Port do odczytu.

## <a name="return-value"></a>Wartość zwracana

Słowa odczytanego z portu.

## <a name="requirements"></a>Wymagania

|Wewnętrzne|Architektura|
|---------------|------------------|
|`__indword`|x86, x64|

**Plik nagłówkowy** \<intrin.h >

## <a name="remarks"></a>Uwagi

Ta procedura jest dostępna wyłącznie jako wewnętrzna.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz też

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)