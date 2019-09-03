---
title: __vmx_vmptrst
ms.date: 09/02/2019
f1_keywords:
- __vmx_vmptrst
helpviewer_keywords:
- __vmx_vmptrst intrinsic
- VMPTRST instruction
ms.assetid: 8dc66e47-03a0-41b0-8e25-c1485f42817a
ms.openlocfilehash: e559746be9e2a3fe5e81afa4d290265394db3e36
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219487"
---
# <a name="__vmx_vmptrst"></a>__vmx_vmptrst

**Microsoft Specific**

Przechowuje wskaźnik do bieżącej struktury sterowania maszyną wirtualną (VMCS) pod określonym adresem.

## <a name="syntax"></a>Składnia

```C
void __vmx_vmptrst(
   unsigned __int64 *VmcsPhysicalAddress
);
```

### <a name="parameters"></a>Parametry

*VmcsPhysicalAddress*\
podczas Adres, w którym jest przechowywany bieżący wskaźnik VMCS.

## <a name="remarks"></a>Uwagi

Wskaźnik VMCS jest 64-bitowym adresem fizycznym.

Funkcja jest równoważna `VMPTRST` z instrukcją maszyny. `__vmx_vmptrst` Ta funkcja obsługuje interakcję z monitorem maszyny wirtualnej hosta z systemem operacyjnym gościa i jego aplikacjami. Aby uzyskać więcej informacji, Wyszukaj dokument "Specyfikacja techniczna wirtualizacji Intel dla architektury Intel o architekturze IA-32", a następnie w witrynie [firmy Intel Corporation](https://software.intel.com/articles/intel-sdm) "numer dokumentu C97063-002".

## <a name="requirements"></a>Wymagania

|Wewnętrznej|Architektura|
|---------------|------------------|
|`__vmx_vmptrst`|x86, x64|

**Plik nagłówka** \<intrin. h >

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)\
[__vmx_vmptrld](../intrinsics/vmx-vmptrld.md)
