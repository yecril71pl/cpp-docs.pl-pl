---
title: __vmx_vmlaunch
ms.date: 09/02/2019
f1_keywords:
- __vmx_vmlaunch
helpviewer_keywords:
- VMLAUNCH instruction
- __vmx_vmlaunch intrinsic
ms.assetid: 708f7c38-b7c1-4ee7-bfc4-0daeb9cc9360
ms.openlocfilehash: 8d78e5181fdd43e10431e12d0cf540c8c9c2e719
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219549"
---
# <a name="__vmx_vmlaunch"></a>__vmx_vmlaunch

**Microsoft Specific**

Umieszcza aplikację wywołującą w niegłównym stanie operacji VMX (Enter VM) przy użyciu bieżącej struktury kontroli maszyny wirtualnej (VMCS).

## <a name="syntax"></a>Składnia

```C
unsigned char __vmx_vmlaunch(void);
```

## <a name="return-value"></a>Wartość zwracana

|Wartość|Znaczenie|
|-----------|-------------|
|0|Operacja zakończyła się pomyślnie.|
|1|Operacja nie powiodła się z rozszerzonym stanem dostępnym w `VM-instruction error field` bieżącym VMCs.|
|2|Operacja nie powiodła się bez dostępnego stanu.|

## <a name="remarks"></a>Uwagi

Aplikacja może wykonać operację wprowadzania do maszyny wirtualnej za pomocą funkcji [__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md) lub [__vmx_vmresume](../intrinsics/vmx-vmresume.md) . Funkcja [__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md) może być używana tylko z VMCs, którego stan uruchamiania to `Clear`, a funkcja [__vmx_vmresume](../intrinsics/vmx-vmresume.md) może być używana tylko z VMCs, którego stanem uruchamiania jest. `Launched` W związku z tym Użyj funkcji [__vmx_vmclear](../intrinsics/vmx-vmclear.md) , aby ustawić stan uruchamiania VMCs na `Clear`, a następnie użyć funkcji [__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md) dla pierwszej operacji VM-Enter i funkcji [__vmx_vmresume](../intrinsics/vmx-vmresume.md) dla kolejnej maszyny wirtualnej — wprowadź składowa.

Funkcja jest równoważna `VMLAUNCH` z instrukcją maszyny. `__vmx_vmlaunch` Ta funkcja obsługuje interakcję z monitorem maszyny wirtualnej hosta z systemem operacyjnym gościa i jego aplikacjami. Aby uzyskać więcej informacji, Wyszukaj dokument "Specyfikacja techniczna wirtualizacji Intel dla architektury Intel o architekturze IA-32", a następnie w witrynie [firmy Intel Corporation](https://software.intel.com/articles/intel-sdm) "numer dokumentu C97063-002".

## <a name="requirements"></a>Wymagania

|Wewnętrznej|Architektura|
|---------------|------------------|
|`__vmx_vmlaunch`|X64|

**Plik nagłówka** \<intrin. h >

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)\
[__vmx_vmresume](../intrinsics/vmx-vmresume.md)\
[__vmx_vmclear](../intrinsics/vmx-vmclear.md)
