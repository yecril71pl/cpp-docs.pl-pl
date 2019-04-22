---
title: __svm_vmload
ms.date: 11/04/2016
f1_keywords:
- __svm_vmload
helpviewer_keywords:
- __svm_vmload intrinsic
- VMLOAD instruction
ms.assetid: b46a5592-db76-4ffc-8694-2f3494e28bed
ms.openlocfilehash: 282f1c005c7eb59b2c590c70b38233c88c664e07
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59031157"
---
# <a name="svmvmload"></a>__svm_vmload

**Microsoft Specific**

Ładuje podzbiór procesor, stan z bloku sterowania określonej maszyny wirtualnej (VMCB).

## <a name="syntax"></a>Składnia

```
void __svm_vmload(
   size_t VmcbPhysicalAddress
);
```

#### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*VmcbPhysicalAddress*|[in] Adres fizyczny VMCB.|

## <a name="remarks"></a>Uwagi

`__svm_vmload` Funkcji jest odpowiednikiem `VMLOAD` machine instrukcji. Ta funkcja obsługuje interakcji monitor maszyny wirtualnej hosta z gościa operacyjnego i jego aplikacji. Aby uzyskać więcej informacji, wyszukaj dokumentu, "AMD64 architektury programisty ręczne woluminie 2: System programowania,"numer 24593, wersji 3.11, dokumentu na [AMD corporation](https://developer.amd.com/resources/developer-guides-manuals/) lokacji.

## <a name="requirements"></a>Wymagania

|Wewnętrzne|Architektura|
|---------------|------------------|
|`__svm_vmload`|x86, x64|

**Plik nagłówkowy** \<intrin.h >

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)<br/>
[__svm_vmrun](../intrinsics/svm-vmrun.md)<br/>
[__svm_vmsave](../intrinsics/svm-vmsave.md)