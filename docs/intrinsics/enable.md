---
title: _enable
ms.date: 09/02/2019
f1_keywords:
- _enable
- _enable_cpp
helpviewer_keywords:
- enable intrinsic
- _enable intrinsic
- ssm instruction
ms.assetid: 8bee669b-6bd8-4e25-9383-bb7d57295b4d
ms.openlocfilehash: 7adcd4eac807b8d0937efbbe6d89f8ad6dcb157c
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217873"
---
# <a name="_enable"></a>_enable

**Microsoft Specific**

Włącza przerwy.

## <a name="syntax"></a>Składnia

```C
void _enable(void);
```

## <a name="requirements"></a>Wymagania

|Wewnętrznej|Architektura|
|---------------|------------------|
|`_enable`|x86, ARM, x64, ARM64|

**Plik nagłówka** \<intrin. h >

## <a name="remarks"></a>Uwagi

`_enable`powoduje, że procesor ustawi flagę przerwania. W systemach x86 ta funkcja generuje instrukcję SET Interrupt flag (`sti`).

Ta funkcja jest dostępna tylko w trybie jądra. W przypadku użycia w trybie użytkownika zostanie zgłoszony wyjątek uprzywilejowanej instrukcji.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)
