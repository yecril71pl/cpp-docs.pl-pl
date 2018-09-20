---
title: __lidt | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __lidt
- __lidt_cpp
dev_langs:
- C++
helpviewer_keywords:
- LIDT instruction
- __lidt intrinsic
ms.assetid: 8298d25d-a19e-4900-828d-6b3b09841882
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f1c2424b949b0276e500b46c34b943b0ef0eb597
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46399122"
---
# <a name="lidt"></a>__lidt

**Microsoft Specific**

Ładuje deskryptora tabeli Rejestr przerwań (IDTR) z wartością w określonej lokalizacji pamięci.

## <a name="syntax"></a>Składnia

```
void __lidt(void * Source);
```

#### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*Źródło*|[in] Wskaźnik do wartości, które mają być kopiowane do IDTR.|

## <a name="requirements"></a>Wymagania

|Wewnętrzne|Architektura|
|---------------|------------------|
|`__lidt`|x86, x64|

**Plik nagłówkowy** \<intrin.h >

## <a name="remarks"></a>Uwagi

`__lidt` Funkcji jest odpowiednikiem `LIDT` komputera instrukcji i jest dostępna tylko w trybie jądra. Aby uzyskać więcej informacji, Wyszukaj w dokumencie "ręcznego deweloper oprogramowania architekturze firmy Intel, wolumin 2: odwołania do zestawu instrukcji," w [Intel Corporation](https://software.intel.com/en-us/articles/intel-sdm) lokacji.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz też

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)<br/>
[__sidt](../intrinsics/sidt.md)