---
title: __readcr4
ms.date: 09/02/2019
f1_keywords:
- __readcr4
helpviewer_keywords:
- __readcr4 intrinsic
ms.assetid: b841a27b-fe0d-4ee9-b76b-f91d3eb061fa
ms.openlocfilehash: 4d43b5204d412de40284f89cfd4d74f1c1f9d86d
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216729"
---
# <a name="__readcr4"></a>__readcr4

**Microsoft Specific**

Odczytuje rejestr CR4 i zwraca jego wartość.

## <a name="syntax"></a>Składnia

```C
unsigned __int64 __readcr4(void);
```

## <a name="return-value"></a>Wartość zwracana

Wartość w rejestrze CR4.

## <a name="requirements"></a>Wymagania

|Wewnętrznej|Architektura|
|---------------|------------------|
|`__readcr4`|x86, x64|

**Plik nagłówka** \<intrin. h >

## <a name="remarks"></a>Uwagi

Element wewnętrzny jest dostępny tylko w trybie jądra, a procedura jest dostępna tylko jako wewnętrzna.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)
