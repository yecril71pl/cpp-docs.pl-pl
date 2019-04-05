---
title: __vmx_vmptrld
ms.date: 11/04/2016
f1_keywords:
- __vmx_vmptrld
helpviewer_keywords:
- __vmx_vmptrld intrinsic
- VMPTRLD instruction
ms.assetid: 95c9ec5b-1a81-41ba-983e-327bd6a65fcb
ms.openlocfilehash: e3d552720d454a4f22af368616b3953452c6db0e
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "59040426"
---
# <a name="vmxvmptrld"></a>__vmx_vmptrld

**Specyficzne dla firmy Microsoft**

Ładuje wskaźnik do bieżącej struktury sterowania maszyny wirtualnej (VMCS) z określonego adresu.

## <a name="syntax"></a>Składnia

```
int __vmx_vmptrld(
   unsigned __int64 *VmcsPhysicalAddress
);
```

### <a name="parameters"></a>Parametry

*VmcsPhysicalAddress*<br/>
[in] Adres, gdzie jest przechowywany wskaźnik VMCS.

## <a name="return-value"></a>Wartość zwracana

0<br/>
Operacja zakończyła się pomyślnie.

1<br/>
Operacja nie powiodła się z rozszerzonych informacji o stanie w `VM-instruction error field` z bieżącym VMCS.

2<br/>
Operacja nie powiodła się bez informacji o stanie.

## <a name="remarks"></a>Uwagi

Wskaźnik VMCS jest 64-bitowy adres fizyczny.

`__vmx_vmptrld` Funkcji jest odpowiednikiem `VMPTRLD` machine instrukcji. Ta funkcja obsługuje interakcji monitor maszyny wirtualnej hosta z gościa operacyjnego i jego aplikacji. Aby uzyskać więcej informacji, wyszukaj dokumentu, "Intel Virtualization Technical Preview specyfikacji dla IA-32 architekturze firmy Intel," dokumentu numer C97063-002 w [Intel Corporation](https://software.intel.com/articles/intel-sdm) lokacji.

## <a name="requirements"></a>Wymagania

|Wewnętrzne|Architektura|
|---------------|------------------|
|`__vmx_vmptrld`|X64|

**Plik nagłówkowy** \<intrin.h >

**KONIEC Specyficzne dla firmy Microsoft**

## <a name="see-also"></a>Zobacz także

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)<br/>
[__vmx_vmptrst](../intrinsics/vmx-vmptrst.md)