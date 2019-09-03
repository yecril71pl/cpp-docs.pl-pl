---
title: __inwordstring
ms.date: 09/02/2019
f1_keywords:
- __inwordstring
- __inwordstring_cpp
helpviewer_keywords:
- __inwordstring intrinsic
- rep insw instruction
ms.assetid: 6de37939-017a-4740-9e3d-7de78a30daba
ms.openlocfilehash: a6f67e15bc5eef9fbe9cc8d12e95afcdf869e3b1
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70221877"
---
# <a name="__inwordstring"></a>__inwordstring

**Microsoft Specific**

Odczytuje dane z określonego portu przy użyciu `rep insw` instrukcji.

## <a name="syntax"></a>Składnia

```C
void __inwordstring(
   unsigned short Port,
   unsigned short* Buffer,
   unsigned long Count
);
```

### <a name="parameters"></a>Parametry

*Przewożąc*\
podczas Port, z którego ma zostać odczytany.

*Buforu*\
określoną Dane odczytane z portu są zapisywane w tym miejscu.

*Liczbą*\
podczas Liczba wyrazów, które mają zostać odczytane.

## <a name="requirements"></a>Wymagania

|Wewnętrznej|Architektura|
|---------------|------------------|
|`__inwordstring`|x86, x64|

**Plik nagłówka** \<intrin. h >

## <a name="remarks"></a>Uwagi

Ta procedura jest dostępna tylko jako wewnętrzna.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)
