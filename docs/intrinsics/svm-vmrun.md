---
title: __svm_vmrun
ms.date: 11/04/2016
f1_keywords:
- __svm_vmrun
helpviewer_keywords:
- __svm_vmrun intrinsic
- VMRUN instruction
ms.assetid: ae98a781-fc17-47b2-b40f-86fcebf1867b
ms.openlocfilehash: 40e53b2ebd54fc109b47f3067e5f89ce50b327de
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "59041062"
---
# <a name="svmvmrun"></a>__svm_vmrun

**Specyficzne dla firmy Microsoft**

Rozpoczyna wykonywanie kodu gościa maszyny wirtualnej, który odnosi się do bloku sterowania określonej maszyny wirtualnej (VMCB).

## <a name="syntax"></a>Składnia

```
void __svm_vmrun(
   size_t VmcbPhysicalAddress
);
```

#### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*VmcbPhysicalAddress*|[in] Adres fizyczny VMCB.|

## <a name="remarks"></a>Uwagi

`__svm_vmrun` Funkcja używa minimalnej ilości informacji w VMCB umożliwiającą wykonywanie kodu gościa maszyny wirtualnej. Użyj [__svm_vmsave](../intrinsics/svm-vmsave.md) lub [__svm_vmload](../intrinsics/svm-vmload.md) działać, jeśli potrzebujesz więcej informacji, do obsługi złożonych przerwania lub przełączyć się do innego gościa.

`__svm_vmrun` Funkcji jest odpowiednikiem `VMRUN` machine instrukcji. Ta funkcja obsługuje interakcji monitor maszyny wirtualnej hosta z gościa operacyjnego i jego aplikacji. Aby uzyskać więcej informacji, wyszukaj dokumentu, "AMD64 architektury programisty ręczne woluminie 2: System programowania,"numer 24593, wersji 3.11 lub później, w dokumentu [AMD corporation](https://developer.amd.com/resources/developer-guides-manuals/) lokacji.

## <a name="requirements"></a>Wymagania

|Wewnętrzne|Architektura|
|---------------|------------------|
|`__svm_vmrun`|x86, x64|

**Plik nagłówkowy** \<intrin.h >

**KONIEC Specyficzne dla firmy Microsoft**

## <a name="see-also"></a>Zobacz także

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)<br/>
[__svm_vmsave](../intrinsics/svm-vmsave.md)<br/>
[__svm_vmload](../intrinsics/svm-vmload.md)