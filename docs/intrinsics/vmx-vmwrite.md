---
title: __vmx_vmwrite
ms.date: 11/04/2016
f1_keywords:
- __vmx_vmwrite
helpviewer_keywords:
- __vmx_vmwrite intrinsic
- VMWRITE instruction
ms.assetid: 88139792-fd3f-4210-97ca-9d84f43a0252
ms.openlocfilehash: e52b1f181f00ce013a111d1a5a62abeff544e20a
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "59037513"
---
# <a name="vmxvmwrite"></a>__vmx_vmwrite

**Specyficzne dla firmy Microsoft**

Zapisuje określoną wartość określonego pola w strukturze kontroli bieżącej maszyny wirtualnej (VMCS).

## <a name="syntax"></a>Składnia

```
unsigned char __vmx_vmwrite(
   size_t Field,
   size_t FieldValue
);
```

#### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*Pole*|[in] Pole VMCS do zapisania.|
|*Wartość FieldValue*|[in] Wartość do zapisania się do pola VMCS.|

## <a name="return-value"></a>Wartość zwracana

0, operacja zakończyła się pomyślnie.

1 operacja nie powiodła się ze stanem rozszerzone jest dostępne w `VM-instruction error field` z bieżącym VMCS.

2. Operacja nie powiodła się bez informacji o stanie.

## <a name="remarks"></a>Uwagi

`__vmx_vmwrite` Funkcji jest odpowiednikiem `VMWRITE` machine instrukcji. Wartość `Field` parametr jest zakodowany indeksu jest opisane w dokumentacji firmy Intel. Aby uzyskać więcej informacji, wyszukaj dokumentu, "Intel Virtualization Technical Preview specyfikacji dla IA-32 architekturze firmy Intel," dokumentu numer C97063-002 w [Intel Corporation](https://software.intel.com/articles/intel-sdm) lokacji, a następnie zapoznaj się z dodatku C dokument.

## <a name="requirements"></a>Wymagania

|Wewnętrzne|Architektura|
|---------------|------------------|
|`__vmx_vmwrite`|X64|

**Plik nagłówkowy** \<intrin.h >

**KONIEC Specyficzne dla firmy Microsoft**

## <a name="see-also"></a>Zobacz także

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)<br/>
[__vmx_vmread](../intrinsics/vmx-vmread.md)