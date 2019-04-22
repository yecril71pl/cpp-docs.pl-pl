---
title: __vmx_vmresume
ms.date: 11/04/2016
f1_keywords:
- __vmx_vmresume
helpviewer_keywords:
- __vmx_vmresume intrinsic
- VMRESUME instruction
ms.assetid: 233fe1b6-c727-493a-a484-1b2363732281
ms.openlocfilehash: d2bfe9a8f98b8a03a82768177217d70674708c39
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59040596"
---
# <a name="vmxvmresume"></a>__vmx_vmresume

**Microsoft Specific**

Wznawia VMX użytkowników innych niż root operacji przy użyciu bieżącej struktury sterowania maszyny wirtualnej (VMCS).

## <a name="syntax"></a>Składnia

```
unsigned char __vmx_vmresume(
   void);
```

## <a name="return-value"></a>Wartość zwracana

|Wartość|Znaczenie|
|-----------|-------------|
|0|Operacja zakończyła się pomyślnie.|
|1|Operacja nie powiodła się z rozszerzonych informacji o stanie w `VM-instruction error field` z bieżącym VMCS.|
|2|Operacja nie powiodła się bez informacji o stanie.|

## <a name="remarks"></a>Uwagi

Aplikacja może wykonywać operację wprowadź maszyny Wirtualnej przy użyciu [__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md) lub `__vmx_vmresume` funkcji. `__vmx_vmlaunch` Funkcji można używać tylko w przypadku VMCS, ma stan uruchomienia `Clear`i `__vmx_vmresume` funkcji można używać tylko w przypadku VMCS, ma stan uruchomienia `Launched`. W związku z tym, użyj [__vmx_vmclear](../intrinsics/vmx-vmclear.md) funkcję, aby ustawić stan uruchomienia VMCS do `Clear`, a następnie użyj `__vmx_vmlaunch` funkcji do pierwszej operacji maszyny Wirtualnej, wprowadź i `__vmx_vmresume` funkcji dla kolejnych wprowadź maszyny Wirtualnej operacje.

`__vmx_vmresume` Funkcji jest odpowiednikiem `VMRESUME` machine instrukcji. Ta funkcja obsługuje interakcji monitor maszyny wirtualnej hosta z gościa operacyjnego i jego aplikacji. Aby uzyskać więcej informacji, wyszukaj dokumentu PDF "Intel Virtualization Technical Preview specyfikacji dla IA-32 architekturze firmy Intel," dokumentu numer C97063-002 w [Intel Corporation](https://software.intel.com/articles/intel-sdm) lokacji.

## <a name="requirements"></a>Wymagania

|Wewnętrzne|Architektura|
|---------------|------------------|
|`__vmx_vmresume`|X64|

**Plik nagłówkowy** \<intrin.h >

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)<br/>
[__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md)<br/>
[__vmx_vmclear](../intrinsics/vmx-vmclear.md)