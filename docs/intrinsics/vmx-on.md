---
title: __vmx_on
ms.date: 09/02/2019
f1_keywords:
- __vmx_on
helpviewer_keywords:
- VMXON instruction
- __vmx_on intrinsic
ms.assetid: 16804991-6a75-4adf-8ec2-bc95acfa4801
ms.openlocfilehash: b6041711d9b6806362b856475151f2c4f63750cb
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219575"
---
# <a name="__vmx_on"></a>__vmx_on

**Microsoft Specific**

Aktywuje operacje rozszerzenia maszyny wirtualnej (VMX) w procesorze.

## <a name="syntax"></a>Składnia

```C
unsigned char __vmx_on(
   unsigned __int64 *VmsSupportPhysicalAddress
);
```

### <a name="parameters"></a>Parametry

*VmsSupportPhysicalAddress*\
podczas Wskaźnik do 64-bitowego adresu fizycznego, który wskazuje na strukturę sterowania maszyną wirtualną (VMCS).

## <a name="return-value"></a>Wartość zwracana

|Wartość|Znaczenie|
|-----------|-------------|
|0|Operacja zakończyła się pomyślnie.|
|1|Operacja nie powiodła się z rozszerzonym stanem dostępnym w `VM-instruction error field` bieżącym VMCs.|
|2|Operacja nie powiodła się bez dostępnego stanu.|

## <a name="remarks"></a>Uwagi

Funkcja odnosi się do instrukcji `VMXON` Machine. `__vmx_on` Ta funkcja obsługuje interakcję z monitorem maszyny wirtualnej hosta z systemem operacyjnym gościa i jego aplikacjami. Aby uzyskać więcej informacji, Wyszukaj dokument "Specyfikacja techniczna wirtualizacji Intel dla architektury Intel o architekturze IA-32", a następnie w witrynie [firmy Intel Corporation](https://software.intel.com/articles/intel-sdm) "numer dokumentu C97063-002".

## <a name="requirements"></a>Wymagania

|Wewnętrznej|Architektura|
|---------------|------------------|
|`__vmx_on`|X64|

**Plik nagłówka** \<intrin. h >

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)
