---
title: __svm_invlpga
ms.date: 11/04/2016
f1_keywords:
- __svm_invlpga
helpviewer_keywords:
- __svm_invlpga intrinsic
- INVLPGA instruction
ms.assetid: aa6578ce-8278-464b-8815-a0fc45330915
ms.openlocfilehash: 5e470fc12ad47aa156c513b293543fa356398d5e
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "59031139"
---
# <a name="svminvlpga"></a>__svm_invlpga

**Specyficzne dla firmy Microsoft**

Unieważnienie wpisu mapowania adresu w buforze aside wygląd tłumaczenia tego komputera. Parametry określają wirtualny adres i adresu miejsca identyfikator strony do unieważnienia.

## <a name="syntax"></a>Składnia

```
void __svm_invlpga(void *Va, int ASID);
```

#### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*Va*|[in] Wirtualny adres strony do unieważnienia.|
|*ASID*|[in] Adres miejsca identyfikator (ASID) strony do unieważnienia.|

## <a name="remarks"></a>Uwagi

`__svm_invlpga` Funkcji jest odpowiednikiem `INVLPGA` machine instrukcji. Ta funkcja obsługuje interakcji monitor maszyny wirtualnej hosta z gościa operacyjnego i jego aplikacji. Aby uzyskać więcej informacji, wyszukaj dokumentu, "AMD64 architektury programisty ręczne woluminie 2: System programowania,"numer 24593, wersji 3.11, dokumentu na [AMD corporation](https://developer.amd.com/resources/developer-guides-manuals/) lokacji.

## <a name="requirements"></a>Wymagania

|Wewnętrzne|Architektura|
|---------------|------------------|
|`__svm_invlpga`|x86, x64|

**Plik nagłówkowy** \<intrin.h >

**KONIEC Specyficzne dla firmy Microsoft**

## <a name="see-also"></a>Zobacz także

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)