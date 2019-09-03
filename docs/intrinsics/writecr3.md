---
title: __writecr3
ms.date: 09/02/2019
f1_keywords:
- _writecr3
helpviewer_keywords:
- _writecr3 intrinsic
ms.assetid: 959d49fa-69d5-47cf-88d2-7688367fe38f
ms.openlocfilehash: f2472a21fe42f10dbf0918480ef02f7e48109747
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219280"
---
# <a name="__writecr3"></a>__writecr3

**Microsoft Specific**

Zapisuje wartość `Data` w rejestrze Cr3.

## <a name="syntax"></a>Składnia

```C
void writecr3(
   unsigned __int64 Data
);
```

### <a name="parameters"></a>Parametry

*Data*\
podczas Wartość, która ma zostać zapisana w rejestrze CR3.

## <a name="requirements"></a>Wymagania

|Wewnętrznej|Architektura|
|---------------|------------------|
|`__writecr3`|x86, x64|

**Plik nagłówka** \<intrin. h >

## <a name="remarks"></a>Uwagi

Ten element wewnętrzny jest dostępny tylko w trybie jądra, a procedura jest dostępna tylko jako wewnętrzna.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)
