---
title: __inbyte
ms.date: 09/02/2019
f1_keywords:
- __inbyte
- __inbyte_cpp
helpviewer_keywords:
- in instruction
- __inbyte intrinsic
ms.assetid: 03b61799-2a08-474d-adc4-2cbf7c81a4d5
ms.openlocfilehash: f0036763ed7315a54fbfe6dcc873b46b52f0730c
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222138"
---
# <a name="__inbyte"></a>__inbyte

**Microsoft Specific**

Generuje instrukcję, zwracając pojedynczy bajt odczytany z portu określonego przez `Port`. `in`

## <a name="syntax"></a>Składnia

```C
unsigned char __inbyte(
   unsigned short Port
);
```

### <a name="parameters"></a>Parametry

*Przewożąc*\
podczas Port, z którego ma zostać odczytany.

## <a name="return-value"></a>Wartość zwracana

Bajt odczytany z określonego portu.

## <a name="requirements"></a>Wymagania

|Wewnętrznej|Architektura|
|---------------|------------------|
|`__inbyte`|x86, x64|

**Plik nagłówka** \<intrin. h >

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="remarks"></a>Uwagi

Ta procedura jest dostępna tylko jako wewnętrzna.

## <a name="see-also"></a>Zobacz także

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)
