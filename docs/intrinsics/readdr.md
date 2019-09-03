---
title: __readdr
ms.date: 09/02/2019
f1_keywords:
- __readdr
helpviewer_keywords:
- __readdr intrinsic
ms.assetid: 061b05da-c85e-4052-b392-106f14bb84f1
ms.openlocfilehash: 646330ca92af08903485fd4583eb2c217fe3e023
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216673"
---
# <a name="__readdr"></a>__readdr

Odczytuje wartość określonego rejestru debugowania.

## <a name="syntax"></a>Składnia

```C
unsigned         __readdr(unsigned int DebugRegister); /* x86 */
unsigned __int64 __readdr(unsigned int DebugRegister); /* x64 */
```

### <a name="parameters"></a>Parametry

*DebugRegister*\
podczas Stała od 0 do 7, która identyfikuje rejestr debugowania.

## <a name="return-value"></a>Wartość zwracana

Wartość określonego rejestru debugowania.

## <a name="remarks"></a>Uwagi

Te elementy wewnętrzne są dostępne tylko w trybie jądra, a procedury są dostępne tylko jako elementy wewnętrzne.

## <a name="requirements"></a>Wymagania

|Wewnętrznej|Architektura|
|---------------|------------------|
|`__readdr`|x86, x64|

**Plik nagłówka** \<intrin. h >

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)\
[__readeflags](../intrinsics/readeflags.md)
