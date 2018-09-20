---
title: __sidt | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __sidt
dev_langs:
- C++
helpviewer_keywords:
- sidt instruction
- __sidt intrinsic
ms.assetid: 01e83d14-6e63-4dea-8f64-5a0339d69641
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dbfb0b50e31cc51c7ea860fbd7b78c89a652ac64
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46429375"
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

`__sidt` Funkcji jest odpowiednikiem `SIDT` machine instrukcji. Aby uzyskać więcej informacji, Wyszukaj w dokumencie "ręcznego deweloper oprogramowania architekturze firmy Intel, wolumin 2: odwołania do zestawu instrukcji," w [Intel Corporation](https://software.intel.com/en-us/articles/intel-sdm) lokacji.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz też

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)<br/>
[__lidt](../intrinsics/lidt.md)