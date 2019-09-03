---
title: __writeeflags
ms.date: 09/02/2019
f1_keywords:
- __writeeflags
helpviewer_keywords:
- __writeeflags intrinsics
ms.assetid: a62a522c-d7fa-4f10-a620-a3b32bdf3f17
ms.openlocfilehash: e43789d2fbed1bdc52665531c61c6c932a27f5ab
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219146"
---
# <a name="__writeeflags"></a>__writeeflags

Zapisuje określoną wartość do rejestru stan programu i kontrola (EFLAGS).

## <a name="syntax"></a>Składnia

```C
void __writeeflags(unsigned Value); /* x86 */
void __writeeflags(unsigned __int64 Value); /* x64 */
```

### <a name="parameters"></a>Parametry

*Wartościami*\
podczas Wartość, która ma zostać zapisana w rejestrze EFLAGS. `Value` Parametr jest 32 bity long dla platformy 32-bitowej i 64 bity long dla platformy 64-bitowej.

## <a name="remarks"></a>Uwagi

Te procedury są dostępne tylko jako elementy wewnętrzne.

## <a name="requirements"></a>Wymagania

|Wewnętrznej|Architektura|
|---------------|------------------|
|`__writeeflags`|x86, x64|

**Plik nagłówka** \<intrin. h >

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)\
[__readeflags](../intrinsics/readeflags.md)
