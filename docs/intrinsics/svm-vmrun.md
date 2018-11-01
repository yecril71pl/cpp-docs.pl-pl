---
title: __svm_vmrun
ms.date: 11/04/2016
f1_keywords:
- __svm_vmrun
helpviewer_keywords:
- __svm_vmrun intrinsic
- VMRUN instruction
ms.assetid: ae98a781-fc17-47b2-b40f-86fcebf1867b
ms.openlocfilehash: ffedf366453a800ce420914376b8d9bb441a602a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50603565"
---
# <a name="svmvmrun"></a>__svm_vmrun

**Microsoft Specific**

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

`__svm_vmrun` Funkcji jest odpowiednikiem `VMRUN` machine instrukcji. Ta funkcja obsługuje interakcji monitor maszyny wirtualnej hosta z gościa operacyjnego i jego aplikacji. Aby uzyskać więcej informacji, wyszukaj dokumentu, "AMD64 architektury programisty ręczne woluminie 2: programowania systemu" dokument o numerze 24593, wersji 3.11 lub później, w [AMD corporation](https://developer.amd.com/resources/developer-guides-manuals/) lokacji.

## <a name="requirements"></a>Wymagania

|Wewnętrzne|Architektura|
|---------------|------------------|
|`__svm_vmrun`|x86, x64|

**Plik nagłówkowy** \<intrin.h >

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz też

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)<br/>
[__svm_vmsave](../intrinsics/svm-vmsave.md)<br/>
[__svm_vmload](../intrinsics/svm-vmload.md)