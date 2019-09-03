---
title: __svm_invlpga
ms.date: 09/02/2019
f1_keywords:
- __svm_invlpga
helpviewer_keywords:
- __svm_invlpga intrinsic
- INVLPGA instruction
ms.assetid: aa6578ce-8278-464b-8815-a0fc45330915
ms.openlocfilehash: e0f8ef02efdb64f70bb65f6f017449fcc03beca1
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219889"
---
# <a name="__svm_invlpga"></a>__svm_invlpga

**Microsoft Specific**

Unieważnia wpis mapowania adresów w buforze przeszukiwania tłumaczenia komputera. Parametry określają adres wirtualny i identyfikator przestrzeni adresowej strony do unieważnienia.

## <a name="syntax"></a>Składnia

```C
void __svm_invlpga(void *Vaddr, int as_id);
```

### <a name="parameters"></a>Parametry

*Vaddr*\
podczas Adres wirtualny strony do unieważnienia.

*as_id*\
podczas Identyfikator przestrzeni adresowej (ASID) strony do unieważnienia.

## <a name="remarks"></a>Uwagi

Funkcja jest równoważna `INVLPGA` z instrukcją maszyny. `__svm_invlpga` Ta funkcja obsługuje interakcję z monitorem maszyny wirtualnej hosta z systemem operacyjnym gościa i jego aplikacjami. Aby uzyskać więcej informacji, Wyszukaj w nim dokument "{Architecture", Tom 2: Programowanie systemu, "numer dokumentu 24593, Poprawka 3,11, w witrynie [AMD Corporation](https://developer.amd.com/resources/developer-guides-manuals/) .

## <a name="requirements"></a>Wymagania

|Wewnętrznej|Architektura|
|---------------|------------------|
|`__svm_invlpga`|x86, x64|

**Plik nagłówka** \<intrin. h >

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)
