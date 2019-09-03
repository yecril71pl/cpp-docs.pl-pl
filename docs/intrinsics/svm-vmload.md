---
title: __svm_vmload
ms.date: 09/02/2019
f1_keywords:
- __svm_vmload
helpviewer_keywords:
- __svm_vmload intrinsic
- VMLOAD instruction
ms.assetid: b46a5592-db76-4ffc-8694-2f3494e28bed
ms.openlocfilehash: da6ca9786b9c7e5041b9a8ca908d567b16176436
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219809"
---
# <a name="__svm_vmload"></a>__svm_vmload

**Microsoft Specific**

Ładuje podzestaw stanu procesora z określonego bloku sterowania maszyną wirtualną (VMCB).

## <a name="syntax"></a>Składnia

```C
void __svm_vmload(
   size_t VmcbPhysicalAddress
);
```

### <a name="parameters"></a>Parametry

*VmcbPhysicalAddress*\
podczas Adres fizyczny VMCB.

## <a name="remarks"></a>Uwagi

Funkcja jest równoważna `VMLOAD` z instrukcją maszyny. `__svm_vmload` Ta funkcja obsługuje interakcję z monitorem maszyny wirtualnej hosta z systemem operacyjnym gościa i jego aplikacjami. Aby uzyskać więcej informacji, Wyszukaj w nim dokument "{Architecture", Tom 2: Programowanie systemu, "numer dokumentu 24593, Poprawka 3,11, w witrynie [AMD Corporation](https://developer.amd.com/resources/developer-guides-manuals/) .

## <a name="requirements"></a>Wymagania

|Wewnętrznej|Architektura|
|---------------|------------------|
|`__svm_vmload`|x86, x64|

**Plik nagłówka** \<intrin. h >

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)\
[__svm_vmrun](../intrinsics/svm-vmrun.md)\
[__svm_vmsave](../intrinsics/svm-vmsave.md)
