---
title: __writeeflags
ms.date: 09/02/2019
f1_keywords:
- __writeeflags
helpviewer_keywords:
- __writeeflags intrinsics
ms.assetid: a62a522c-d7fa-4f10-a620-a3b32bdf3f17
ms.openlocfilehash: 6b9b6976369ed810789e5749a2e30029cad4c2d7
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2019
ms.locfileid: "74858051"
---
# <a name="__writeeflags"></a>__writeeflags

**Microsoft Specific**

Zapisuje określoną wartość do rejestru stan programu i kontrola (EFLAGS).

## <a name="syntax"></a>Składnia

```C
void __writeeflags(unsigned Value); /* x86 */
void __writeeflags(unsigned __int64 Value); /* x64 */
```

### <a name="parameters"></a>Parametry

\ *wartości*
podczas Wartość, która ma zostać zapisana w rejestrze EFLAGS. Parametr `Value` to 32 bitów Long dla platformy 32-bitowej i 64 bity long dla platformy 64-bitowej.

## <a name="remarks"></a>Uwagi

Te procedury są dostępne tylko jako elementy wewnętrzne.

## <a name="requirements"></a>Wymagania

|Wewnętrzne|Architektura|
|---------------|------------------|
|`__writeeflags`|x86, x64|

**Plik nagłówkowy** \<intrin. h >

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

\ [Wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)
[__readeflags](../intrinsics/readeflags.md)
