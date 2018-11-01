---
title: __inword
ms.date: 11/04/2016
f1_keywords:
- __indword_cpp
- __indword
helpviewer_keywords:
- in instruction
- __inword intrinsic
ms.assetid: 5c617edd-6709-40a1-aad2-40d5e39283c6
ms.openlocfilehash: 85498fd85f5401ad123794cc9aaed2b278db867c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50475364"
---
# <a name="inword"></a>__inword

**Microsoft Specific**

Odczytuje dane z określonego portu przy użyciu `in` instrukcji.

## <a name="syntax"></a>Składnia

```
unsigned short __inword(
   unsigned short Port
);
```

#### <a name="parameters"></a>Parametry

*Port*<br/>
[in] Port do odczytu.

## <a name="return-value"></a>Wartość zwracana

Word danych do odczytu.

## <a name="requirements"></a>Wymagania

|Wewnętrzne|Architektura|
|---------------|------------------|
|`__inword`|x86, x64|

**Plik nagłówkowy** \<intrin.h >

## <a name="remarks"></a>Uwagi

Ta procedura jest dostępna wyłącznie jako wewnętrzna.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz też

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)