---
title: __svm_stgi
ms.date: 11/04/2016
f1_keywords:
- __svm_stgi
helpviewer_keywords:
- __svm_stgi intrinsic
- STGI instruction
ms.assetid: 96488da4-5587-4e99-8674-627a9e51be84
ms.openlocfilehash: 9f7e35bbecf4051e4a47c32753b3a221dd2a4cc1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50494695"
---
# <a name="svmstgi"></a>__svm_stgi

**Microsoft Specific**

Ustawia flagi globalnej przerwania.

## <a name="syntax"></a>Składnia

```
void __svm_stgi(void);
```

## <a name="remarks"></a>Uwagi

`__svm_stgi` Funkcji jest odpowiednikiem `STGI` machine instrukcji. Flagi globalnej przerwania określa, czy procesor ignoruje, odłoży czy obsługi przerwań z powodu zdarzenia, takie jak ukończenia operacji We/Wy, alert temperatury sprzętu lub wyjątek debugowania.

Ta funkcja obsługuje interakcji monitor maszyny wirtualnej hosta z gościa operacyjnego i jego aplikacji. Aby uzyskać więcej informacji, wyszukaj dokumentu, "AMD64 architektury programisty ręczne woluminie 2: programowania systemu" numer 24593, wersji 3.11, dokumentu w [AMD corporation](https://developer.amd.com/resources/developer-guides-manuals/) lokacji.

## <a name="requirements"></a>Wymagania

|Wewnętrzne|Architektura|
|---------------|------------------|
|`__svm_stgi`|x86, x64|

**Plik nagłówkowy** \<intrin.h >

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz też

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)<br/>
[__svm_clgi](../intrinsics/svm-clgi.md)