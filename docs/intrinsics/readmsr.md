---
title: __readmsr
ms.date: 11/04/2016
f1_keywords:
- __readmsr
helpviewer_keywords:
- Read Model Specific Register
- rdmsr instruction
- __readmsr intrinsic
ms.assetid: 7ab1f8e8-72cb-4ce4-817d-3e728a3c9716
ms.openlocfilehash: 45e9c21eb8d9ac213812236a91c050c3c9df8f8d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50641067"
---
# <a name="readmsr"></a>__readmsr

**Microsoft Specific**

Generuje `rdmsr` instrukcji, który odczytuje rejestru specyficzne dla modelu, określony przez `register` i zwraca jego wartość.

## <a name="syntax"></a>Składnia

```
__int64 __readmsr( 
   int register 
);
```

#### <a name="parameters"></a>Parametry

*register*<br/>
[in] Rejestr określonego modelu do odczytu.

## <a name="return-value"></a>Wartość zwracana

Wartość do określonego rejestru.

## <a name="requirements"></a>Wymagania

|Wewnętrzne|Architektura|
|---------------|------------------|
|`__readmsr`|x86, x64|

**Plik nagłówkowy** \<intrin.h >

## <a name="remarks"></a>Uwagi

Ta funkcja jest dostępna tylko w trybie jądra, a procedura jest dostępna jako funkcja wewnętrzna tylko.

Aby uzyskać więcej informacji zobacz dokumentację AMD.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz też

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)