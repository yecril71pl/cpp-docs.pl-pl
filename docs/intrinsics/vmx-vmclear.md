---
title: __vmx_vmclear
ms.date: 09/02/2019
f1_keywords:
- __vmx_vmclear
helpviewer_keywords:
- VMCLEAR instruction
- __vmx_vmclear intrinsic
ms.assetid: e3eb98e4-50fc-4c93-9bac-340fd1f0a466
ms.openlocfilehash: 3b5807402cf0a9d8a9ef1ded1d112d22a801633e
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219542"
---
# <a name="__vmx_vmclear"></a>__vmx_vmclear

**Microsoft Specific**

Inicjuje określoną strukturę sterowania maszyną wirtualną (VMCS) i ustawia jej stan uruchamiania na `Clear`.

## <a name="syntax"></a>Składnia

```C
unsigned char __vmx_vmclear(
   unsigned __int64 *VmcsPhysicalAddress
);
```

### <a name="parameters"></a>Parametry

*VmcsPhysicalAddress*\
podczas Wskaźnik do 64-bitowej lokalizacji pamięci, która zawiera adres fizyczny VMCS do wyczyszczenia.

## <a name="return-value"></a>Wartość zwracana

|Wartość|Znaczenie|
|-----------|-------------|
|0|Operacja zakończyła się pomyślnie.|
|1|Operacja nie powiodła się z rozszerzonym stanem dostępnym w `VM-instruction error field` bieżącym VMCs.|
|2|Operacja nie powiodła się bez dostępnego stanu.|

## <a name="remarks"></a>Uwagi

Aplikacja może wykonać operację wprowadzania do maszyny wirtualnej za pomocą funkcji [__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md) lub [__vmx_vmresume](../intrinsics/vmx-vmresume.md) . Funkcja [__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md) może być używana tylko z VMCs, którego stan uruchamiania to `Clear`, a funkcja [__vmx_vmresume](../intrinsics/vmx-vmresume.md) może być używana tylko z VMCs, którego stanem uruchamiania jest. `Launched` W związku z tym Użyj funkcji [__vmx_vmclear](../intrinsics/vmx-vmclear.md) , aby ustawić stan uruchamiania elementu VMCs na `Clear`. Użyj funkcji [__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md) dla pierwszej operacji VM-Enter i funkcji [__vmx_vmresume](../intrinsics/vmx-vmresume.md) dla kolejnych maszyn wirtualnych — wprowadź operacje.

Funkcja jest równoważna `VMCLEAR` z instrukcją maszyny. `__vmx_vmclear` Ta funkcja obsługuje interakcję z monitorem maszyny wirtualnej hosta z systemem operacyjnym gościa i jego aplikacjami. Aby uzyskać więcej informacji, Wyszukaj dokument "Specyfikacja techniczna wirtualizacji Intel dla architektury Intel o architekturze IA-32", a następnie w witrynie [firmy Intel Corporation](https://software.intel.com/articles/intel-sdm) "numer dokumentu C97063-002".

## <a name="requirements"></a>Wymagania

|Wewnętrznej|Architektura|
|---------------|------------------|
|`__vmx_vmclear`|X64|

**Plik nagłówka** \<intrin. h >

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)\
[__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md)\
[__vmx_vmresume](../intrinsics/vmx-vmresume.md)
