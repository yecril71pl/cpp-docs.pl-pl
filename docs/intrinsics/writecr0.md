---
title: __writecr0
ms.date: 09/02/2019
f1_keywords:
- _writecr0
helpviewer_keywords:
- _writecr0 intrinsic
ms.assetid: a143d08d-0333-4e1b-91b4-4acb2ae91b5a
ms.openlocfilehash: 1f00796242ae352d32935c2551d50f2d93d734ec
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219302"
---
# <a name="__writecr0"></a>__writecr0

**Microsoft Specific**

Zapisuje wartość `Data` w rejestrze CR0.

## <a name="syntax"></a>Składnia

```C
void writecr0(
   unsigned __int64 Data
);
```

### <a name="parameters"></a>Parametry

*Data*\
podczas Wartość, która ma zostać zapisana w rejestrze CR0.

## <a name="requirements"></a>Wymagania

|Wewnętrznej|Architektura|
|---------------|------------------|
|`__writecr0`|x86, x64|

**Plik nagłówka** \<intrin. h >

## <a name="remarks"></a>Uwagi

Ten element wewnętrzny jest dostępny tylko w trybie jądra, a procedura jest dostępna tylko jako wewnętrzna.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)
