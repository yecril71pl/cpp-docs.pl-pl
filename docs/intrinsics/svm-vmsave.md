---
title: __svm_vmsave
ms.date: 09/02/2019
f1_keywords:
- __svm_vmsave
helpviewer_keywords:
- VMSAVE instruction
- __svm_vmsave intrinsic
ms.assetid: 617a60bd-8514-4ba1-8066-bcf4dd481030
ms.openlocfilehash: f91efa7116a8a8e9ebe27c7e5e4e64c4f1533e9d
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219798"
---
# <a name="__svm_vmsave"></a>__svm_vmsave

**Microsoft Specific**

Przechowuje podzestaw stanu procesora w określonym bloku sterowania maszyną wirtualną (VMCB).

## <a name="syntax"></a>Składnia

```C
void __svm_vmsave(
   size_t VmcbPhysicalAddress
);
```

### <a name="parameters"></a>Parametry

*VmcbPhysicalAddress*\
podczas Adres fizyczny VMCB.

## <a name="remarks"></a>Uwagi

Funkcja jest równoważna `VMSAVE` z instrukcją maszyny. `__svm_vmsave` Ta funkcja obsługuje interakcję z monitorem maszyny wirtualnej hosta z systemem operacyjnym gościa i jego aplikacjami. Aby uzyskać więcej informacji, Wyszukaj w nim dokument "{Architecture", Tom 2: Programowanie systemu, "dokument numer 24593, wersja 3,11 lub nowsza" w witrynie [AMD Corporation](https://developer.amd.com/resources/developer-guides-manuals/) .

## <a name="requirements"></a>Wymagania

|Wewnętrznej|Architektura|
|---------------|------------------|
|`__svm_vmsave`|x86, x64|

**Plik nagłówka** \<intrin. h >

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)\
[__svm_vmrun](../intrinsics/svm-vmrun.md)\
[__svm_vmload](../intrinsics/svm-vmload.md)
