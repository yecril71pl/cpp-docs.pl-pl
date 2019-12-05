---
title: __readeflags
ms.date: 09/02/2019
f1_keywords:
- __readeflags
helpviewer_keywords:
- __readeflags intrinsic
ms.assetid: f9d2f4d8-c428-491f-b8de-04d0566b2b6b
ms.openlocfilehash: 6afdc0f20a3ae72865a80ba2eb7f896f79f63171
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857908"
---
# <a name="__readeflags"></a>__readeflags

**Microsoft Specific**

Odczytuje dane rejestru stan programu i kontrola (EFLAGS).

## <a name="syntax"></a>Składnia

```C
unsigned     int __readeflags(void); /* x86 */
unsigned __int64 __readeflags(void); /* x64 */
```

## <a name="return-value"></a>Wartość zwracana

Wartość rejestru EFLAGS. Wartość zwracana to 32 bitów na platformie 32-bitowej i 64 bitów na platformie 64-bitowej.

## <a name="remarks"></a>Uwagi

Te procedury są dostępne tylko jako elementy wewnętrzne.

## <a name="requirements"></a>Wymagania

|Wewnętrzne|Architektura|
|---------------|------------------|
|`__readeflags`|x86, x64|

**Plik nagłówkowy** \<intrin. h >

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

\ [Wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)
[__writeeflags](../intrinsics/writeeflags.md)
