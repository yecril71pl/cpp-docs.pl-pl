---
title: __vmx_vmwrite
ms.date: 09/02/2019
f1_keywords:
- __vmx_vmwrite
helpviewer_keywords:
- __vmx_vmwrite intrinsic
- VMWRITE instruction
ms.assetid: 88139792-fd3f-4210-97ca-9d84f43a0252
ms.openlocfilehash: cdc5590858f160db24bf75ef11c8f20b204a3152
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219390"
---
# <a name="__vmx_vmwrite"></a>__vmx_vmwrite

**Microsoft Specific**

Zapisuje określoną wartość do określonego pola w bieżącej strukturze sterowania maszyną wirtualną (VMCS).

## <a name="syntax"></a>Składnia

```C
unsigned char __vmx_vmwrite(
   size_t Field,
   size_t FieldValue
);
```

### <a name="parameters"></a>Parametry

*Polami*\
podczas Pole VMCS, które ma zostać zapisane.

*FieldValue*\
podczas Wartość do zapisu w polu VMCS.

## <a name="return-value"></a>Wartość zwracana

0\
Operacja zakończyła się pomyślnie.

1\
Operacja nie powiodła się z rozszerzonym stanem dostępnym w `VM-instruction error field` bieżącym VMCs.

2\
Operacja nie powiodła się bez dostępnego stanu.

## <a name="remarks"></a>Uwagi

Funkcja jest równoważna `VMWRITE` z instrukcją maszyny. `__vmx_vmwrite` Wartość `Field` parametru jest zakodowanym indeksem pola, który jest opisany w dokumentacji firmy Intel. Aby uzyskać więcej informacji, Wyszukaj dodatek C "Specyfikacja techniczna wirtualizacji firmy Intel dla architektury Intel o architekturze IA-32" w witrynie [Intel Corporation](https://software.intel.com/articles/intel-sdm) .

## <a name="requirements"></a>Wymagania

|Wewnętrznej|Architektura|
|---------------|------------------|
|`__vmx_vmwrite`|X64|

**Plik nagłówka** \<intrin. h >

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)\
[__vmx_vmread](../intrinsics/vmx-vmread.md)
