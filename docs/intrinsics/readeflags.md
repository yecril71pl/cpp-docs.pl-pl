---
title: __readeflags
ms.date: 11/04/2016
f1_keywords:
- __readeflags
helpviewer_keywords:
- __readeflags intrinsic
ms.assetid: f9d2f4d8-c428-491f-b8de-04d0566b2b6b
ms.openlocfilehash: e5294180904d0d7ca3bbd1de75e45e058a33c88f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50594275"
---
# <a name="readeflags"></a>__readeflags

Odczytuje stan programu i kontroli (EFLAGS) do rejestru.

## <a name="syntax"></a>Składnia

```
unsigned     int __readeflags(void);
unsigned __int64 __readeflags(void);
```

## <a name="return-value"></a>Wartość zwracana

Wartość rejestru EFLAGS. Wartość zwracana wynosi 32-bitowy, czas na platformie 32-bitowych i 64-bitowy długo na platformie 64-bitowych.

## <a name="remarks"></a>Uwagi

Te procedury są dostępne tylko jako funkcje wewnętrzne.

## <a name="requirements"></a>Wymagania

|Wewnętrzne|Architektura|
|---------------|------------------|
|`__readeflags`|x86, x64|

**Plik nagłówkowy** \<intrin.h >

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz też

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)<br/>
[__writeeflags](../intrinsics/writeeflags.md)