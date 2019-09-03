---
title: __writecr4
ms.date: 09/02/2019
f1_keywords:
- _writecr4
helpviewer_keywords:
- _writecr4 intrinsic
ms.assetid: ab7651d7-b86b-4be7-a0a0-7263099c70fc
ms.openlocfilehash: 1afdadcdfdbf1060c87e3865dd5597b0b9a2ea6b
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219267"
---
# <a name="__writecr4"></a>__writecr4

**Microsoft Specific**

Zapisuje wartość `Data` w rejestrze CR4.

## <a name="syntax"></a>Składnia

```C
void writecr4(
   unsigned __int64 Data
);
```

### <a name="parameters"></a>Parametry

*Data*\
podczas Wartość, która ma zostać zapisana w rejestrze CR4.

## <a name="requirements"></a>Wymagania

|Wewnętrznej|Architektura|
|---------------|------------------|
|`__writecr4`|x86, x64|

**Plik nagłówka** \<intrin. h >

## <a name="remarks"></a>Uwagi

Ten element wewnętrzny jest dostępny tylko w trybie jądra, a procedura jest dostępna tylko jako wewnętrzna.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)
