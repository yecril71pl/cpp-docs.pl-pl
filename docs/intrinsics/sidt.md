---
title: __sidt
ms.date: 11/04/2016
f1_keywords:
- __sidt
helpviewer_keywords:
- sidt instruction
- __sidt intrinsic
ms.assetid: 01e83d14-6e63-4dea-8f64-5a0339d69641
ms.openlocfilehash: 2188b2cdbf5c5f8836197f8cf2ee33928b7e9425
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50624461"
---
# <a name="sidt"></a>__sidt

**Microsoft Specific**

Przechowuje wartość rejestru Tabela deskryptora przerwania (IDTR) w określonej lokalizacji pamięci.

## <a name="syntax"></a>Składnia

```
void __sidt(void * Destination);
```

#### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*miejsce docelowe*|[in] Wskaźnik do przechowywania IDTR lokalizacji w pamięci.|

## <a name="requirements"></a>Wymagania

|Wewnętrzne|Architektura|
|---------------|------------------|
|`__sidt`|x86, x64|

**Plik nagłówkowy** \<intrin.h >

## <a name="remarks"></a>Uwagi

`__sidt` Funkcji jest odpowiednikiem `SIDT` machine instrukcji. Aby uzyskać więcej informacji, Wyszukaj w dokumencie "ręcznego deweloper oprogramowania architekturze firmy Intel, wolumin 2: odwołania do zestawu instrukcji," w [Intel Corporation](https://software.intel.com/articles/intel-sdm) lokacji.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz też

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)<br/>
[__lidt](../intrinsics/lidt.md)