---
title: __writedr
ms.date: 09/02/2019
f1_keywords:
- __writedr
helpviewer_keywords:
- __writedr intrinsic
ms.assetid: ac55c1ee-df2f-41d4-a429-6f369d2a934d
ms.openlocfilehash: 473e7223e9974d0125e772c152ea85ae90b97342
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2019
ms.locfileid: "74858064"
---
# <a name="__writedr"></a>__writedr

**Microsoft Specific**

Zapisuje określoną wartość do określonego rejestru debugowania.

## <a name="syntax"></a>Składnia

```C
void __writedr(unsigned DebugRegister, unsigned DebugValue); /* x86 */
void __writedr(unsigned DebugRegister, unsigned __int64 DebugValue); /* x64 */
```

### <a name="parameters"></a>Parametry

*DebugRegister*\
podczas Liczba od 0 do 7, która identyfikuje rejestr debugowania.

*DebugValue*\
podczas Wartość do zapisu w rejestrze debugowania.

## <a name="remarks"></a>Uwagi

Te elementy wewnętrzne są dostępne tylko w trybie jądra, a procedury są dostępne tylko jako elementy wewnętrzne.

## <a name="requirements"></a>Wymagania

|Wewnętrzne|Architektura|
|---------------|------------------|
|`__writedr`|x86, x64|

**Plik nagłówkowy** \<intrin. h >

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

\ [Wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)
[__readdr](../intrinsics/readdr.md)
