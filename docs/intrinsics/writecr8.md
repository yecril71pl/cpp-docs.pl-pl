---
title: __writecr8
ms.date: 09/02/2019
f1_keywords:
- _writecr8
helpviewer_keywords:
- _writecr8 intrinsic
ms.assetid: 6f8bd632-dddb-4335-971e-1acee24aa2b9
ms.openlocfilehash: c8df13c15b5cd8a51b77d65ad930a1852809ee30
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219236"
---
# <a name="__writecr8"></a>__writecr8

**Microsoft Specific**

Zapisuje wartość `Data` w rejestrze CR8.

## <a name="syntax"></a>Składnia

```C
void writecr8(
   unsigned __int64 Data
);
```

### <a name="parameters"></a>Parametry

*Data*\
podczas Wartość, która ma zostać zapisana w rejestrze CR8.

## <a name="requirements"></a>Wymagania

|Wewnętrznej|Architektura|
|---------------|------------------|
|`__writecr8`|X64|

**Plik nagłówka** \<intrin. h >

## <a name="remarks"></a>Uwagi

Element `__writecr8` wewnętrzny jest dostępny tylko w trybie jądra, a procedura jest dostępna tylko jako wewnętrzna.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)
