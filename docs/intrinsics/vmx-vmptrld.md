---
title: __vmx_vmptrld
ms.date: 09/02/2019
f1_keywords:
- __vmx_vmptrld
helpviewer_keywords:
- __vmx_vmptrld intrinsic
- VMPTRLD instruction
ms.assetid: 95c9ec5b-1a81-41ba-983e-327bd6a65fcb
ms.openlocfilehash: 79b5a8b34b652ae1f011e89c793a7157c9e435ee
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219494"
---
# <a name="__vmx_vmptrld"></a>__vmx_vmptrld

**Microsoft Specific**

Ładuje wskaźnik do bieżącej struktury kontroli maszyny wirtualnej (VMCS) z podanego adresu.

## <a name="syntax"></a>Składnia

```C
int __vmx_vmptrld(
   unsigned __int64 *VmcsPhysicalAddress
);
```

### <a name="parameters"></a>Parametry

*VmcsPhysicalAddress*\
podczas Adres, w którym jest przechowywany wskaźnik VMCS.

## <a name="return-value"></a>Wartość zwracana

0\
Operacja zakończyła się pomyślnie.

1\
Operacja nie powiodła się z rozszerzonym stanem dostępnym w `VM-instruction error field` bieżącym VMCs.

2\
Operacja nie powiodła się bez dostępnego stanu.

## <a name="remarks"></a>Uwagi

Wskaźnik VMCS jest 64-bitowym adresem fizycznym.

Funkcja jest równoważna `VMPTRLD` z instrukcją maszyny. `__vmx_vmptrld` Ta funkcja obsługuje interakcję z monitorem maszyny wirtualnej hosta z systemem operacyjnym gościa i jego aplikacjami. Aby uzyskać więcej informacji, Wyszukaj dokument "Specyfikacja techniczna wirtualizacji Intel dla architektury Intel o architekturze IA-32", a następnie w witrynie [firmy Intel Corporation](https://software.intel.com/articles/intel-sdm) "numer dokumentu C97063-002".

## <a name="requirements"></a>Wymagania

|Wewnętrznej|Architektura|
|---------------|------------------|
|`__vmx_vmptrld`|X64|

**Plik nagłówka** \<intrin. h >

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)\
[__vmx_vmptrst](../intrinsics/vmx-vmptrst.md)
