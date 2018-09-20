---
title: __vmx_vmptrst | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __vmx_vmptrst
dev_langs:
- C++
helpviewer_keywords:
- __vmx_vmptrst intrinsic
- VMPTRST instruction
ms.assetid: 8dc66e47-03a0-41b0-8e25-c1485f42817a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ccd691edb9ee799c8585fb33cb6b837e2871fc36
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46413979"
---
# <a name="vmxvmptrst"></a>__vmx_vmptrst

**Microsoft Specific**

Przechowuje wskaźnik do bieżącej struktury sterowania maszyny wirtualnej (VMCS) pod podanym adresem.

## <a name="syntax"></a>Składnia

```
void __vmx_vmptrst( 
   unsigned __int64 *VmcsPhysicalAddress 
);
```

#### <a name="parameters"></a>Parametry

[w] *`VmcsPhysicalAddress` adresu, gdzie znajduje się bieżący wskaźnik VMCS.

## <a name="remarks"></a>Uwagi

Wskaźnik VMCS jest 64-bitowy adres fizyczny.

`__vmx_vmptrst` Funkcji jest odpowiednikiem `VMPTRST` machine instrukcji. Ta funkcja obsługuje interakcji monitor maszyny wirtualnej hosta z gościa operacyjnego i jego aplikacji. Aby uzyskać więcej informacji, wyszukaj dokumentu, "Intel Virtualization Technical Preview specyfikacji dla IA-32 architekturze firmy Intel," dokumentu numer C97063-002 w [Intel Corporation](https://software.intel.com/en-us/articles/intel-sdm) lokacji.

## <a name="requirements"></a>Wymagania

|Wewnętrzne|Architektura|
|---------------|------------------|
|`__vmx_vmptrst`|x86, x64|

**Plik nagłówkowy** \<intrin.h >

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz też

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)<br/>
[__vmx_vmptrld](../intrinsics/vmx-vmptrld.md)