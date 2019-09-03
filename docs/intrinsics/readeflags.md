---
title: __readeflags
ms.date: 09/02/2019
f1_keywords:
- __readeflags
helpviewer_keywords:
- __readeflags intrinsic
ms.assetid: f9d2f4d8-c428-491f-b8de-04d0566b2b6b
ms.openlocfilehash: fe2365c2837b6c583810bb9fc908fe98486a2d38
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70221227"
---
# <a name="__readeflags"></a>__readeflags

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

|Wewnętrznej|Architektura|
|---------------|------------------|
|`__readeflags`|x86, x64|

**Plik nagłówka** \<intrin. h >

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)\
[__writeeflags](../intrinsics/writeeflags.md)
