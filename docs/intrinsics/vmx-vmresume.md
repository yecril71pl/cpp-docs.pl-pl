---
title: __vmx_vmresume
ms.date: 09/02/2019
f1_keywords:
- __vmx_vmresume
helpviewer_keywords:
- __vmx_vmresume intrinsic
- VMRESUME instruction
ms.assetid: 233fe1b6-c727-493a-a484-1b2363732281
ms.openlocfilehash: 34d0e6814dd00da07076e644513400bd5be36bd3
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219450"
---
# <a name="__vmx_vmresume"></a>__vmx_vmresume

**Microsoft Specific**

Wznawia operację niegłówną VMX przy użyciu bieżącej struktury kontrolnej maszyny wirtualnej (VMCS).

## <a name="syntax"></a>Składnia

```C
unsigned char __vmx_vmresume(
   void);
```

## <a name="return-value"></a>Wartość zwracana

|Wartość|Znaczenie|
|-----------|-------------|
|0|Operacja zakończyła się pomyślnie.|
|1|Operacja nie powiodła się z rozszerzonym stanem dostępnym w `VM-instruction error field` bieżącym VMCs.|
|2|Operacja nie powiodła się bez dostępnego stanu.|

## <a name="remarks"></a>Uwagi

Aplikacja może wykonać operację wprowadzania do maszyny wirtualnej za pomocą funkcji [__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md) lub `__vmx_vmresume` . Funkcja może być używana tylko z VMCs o `Clear`stanie uruchamiania, a `__vmx_vmresume` funkcja może być używana tylko z VMCs, którego stanem uruchamiania jest `Launched`. `__vmx_vmlaunch` W związku z tym Użyj funkcji [__vmx_vmclear](../intrinsics/vmx-vmclear.md) , aby ustawić stan uruchamiania VMCs na `Clear`, `__vmx_vmlaunch` a następnie użyć funkcji dla `__vmx_vmresume` pierwszej maszyny wirtualnej — wprowadź operację i funkcję dla kolejnych maszyn wirtualnych — wprowadź operacje.

Funkcja jest równoważna `VMRESUME` z instrukcją maszyny. `__vmx_vmresume` Ta funkcja obsługuje interakcję z monitorem maszyny wirtualnej hosta z systemem operacyjnym gościa i jego aplikacjami. Aby uzyskać więcej informacji, Wyszukaj dokument PDF "Specyfikacja techniczna wirtualizacji Intel dla architektury Intel o architekturze IA-32" w witrynie [firmy Intel Corporation](https://software.intel.com/articles/intel-sdm) "numer dokumentu C97063-002.

## <a name="requirements"></a>Wymagania

|Wewnętrznej|Architektura|
|---------------|------------------|
|`__vmx_vmresume`|X64|

**Plik nagłówka** \<intrin. h >

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)\
[__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md)\
[__vmx_vmclear](../intrinsics/vmx-vmclear.md)
