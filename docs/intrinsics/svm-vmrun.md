---
title: __svm_vmrun
ms.date: 09/02/2019
f1_keywords:
- __svm_vmrun
helpviewer_keywords:
- __svm_vmrun intrinsic
- VMRUN instruction
ms.assetid: ae98a781-fc17-47b2-b40f-86fcebf1867b
ms.openlocfilehash: f23df894cc8ad1c270c4c0acbc97cab727e47d93
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219823"
---
# <a name="__svm_vmrun"></a>__svm_vmrun

**Microsoft Specific**

Uruchamia wykonywanie kodu gościa maszyny wirtualnej odpowiadającego określonemu blokowi sterowania maszynom wirtualnym (VMCB).

## <a name="syntax"></a>Składnia

```C
void __svm_vmrun(
   size_t VmcbPhysicalAddress
);
```

### <a name="parameters"></a>Parametry

*VmcbPhysicalAddress*\
podczas Adres fizyczny VMCB.

## <a name="remarks"></a>Uwagi

`__svm_vmrun` Funkcja używa minimalnej ilości informacji w VMCB, aby rozpocząć wykonywanie kodu gościa maszyny wirtualnej. Użyj funkcji [__svm_vmsave](../intrinsics/svm-vmsave.md) lub [__svm_vmload](../intrinsics/svm-vmload.md) , jeśli potrzebujesz więcej informacji do obsługi złożonego przerwania lub przełączenia się do innego gościa.

Funkcja jest równoważna `VMRUN` z instrukcją maszyny. `__svm_vmrun` Ta funkcja obsługuje interakcję z monitorem maszyny wirtualnej hosta z systemem operacyjnym gościa i jego aplikacjami. Aby uzyskać więcej informacji, Wyszukaj w nim dokument "{Architecture", Tom 2: Programowanie systemu, "dokument numer 24593, wersja 3,11 lub nowsza" w witrynie [AMD Corporation](https://developer.amd.com/resources/developer-guides-manuals/) .

## <a name="requirements"></a>Wymagania

|Wewnętrznej|Architektura|
|---------------|------------------|
|`__svm_vmrun`|x86, x64|

**Plik nagłówka** \<intrin. h >

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)\
[__svm_vmsave](../intrinsics/svm-vmsave.md)\
[__svm_vmload](../intrinsics/svm-vmload.md)
