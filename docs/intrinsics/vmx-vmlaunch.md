---
title: __vmx_vmlaunch
ms.date: 11/04/2016
f1_keywords:
- __vmx_vmlaunch
helpviewer_keywords:
- VMLAUNCH instruction
- __vmx_vmlaunch intrinsic
ms.assetid: 708f7c38-b7c1-4ee7-bfc4-0daeb9cc9360
ms.openlocfilehash: 70c26da61d1ba9a8e5dc52d6fb0318fad918f525
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50512998"
---
# <a name="vmxvmlaunch"></a>__vmx_vmlaunch

**Microsoft Specific**

Umieszczanie aplikacji wywołującej stan inny niż główny operacji VMX (wprowadź maszyny Wirtualnej) przy użyciu bieżącej struktury sterowania maszyny wirtualnej (VMCS).

## <a name="syntax"></a>Składnia

```
unsigned char __vmx_vmlaunch(
   void);
```

## <a name="return-value"></a>Wartość zwracana

|Wartość|Znaczenie|
|-----------|-------------|
|0|Operacja zakończyła się pomyślnie.|
|1|Operacja nie powiodła się z rozszerzonych informacji o stanie w `VM-instruction error field` z bieżącym VMCS.|
|2|Operacja nie powiodła się bez informacji o stanie.|

## <a name="remarks"></a>Uwagi

Aplikacja może wykonywać operację wprowadź maszyny Wirtualnej przy użyciu [__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md) lub [__vmx_vmresume](../intrinsics/vmx-vmresume.md) funkcji. [__Vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md) funkcji można używać tylko w przypadku VMCS, ma stan uruchomienia `Clear`i [__vmx_vmresume](../intrinsics/vmx-vmresume.md) funkcji można używać tylko w przypadku VMCS, ma stan uruchomienia `Launched`. W związku z tym, użyj [__vmx_vmclear](../intrinsics/vmx-vmclear.md) funkcję, aby ustawić stan uruchomienia VMCS do `Clear`, a następnie za pomocą [__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md) funkcja pierwszą operacją wprowadź maszyny Wirtualnej i [__vmx_vmresume](../intrinsics/vmx-vmresume.md) funkcji dla kolejnych operacji wprowadź maszyny Wirtualnej.

`__vmx_vmlaunch` Funkcji jest odpowiednikiem `VMLAUNCH` machine instrukcji. Ta funkcja obsługuje interakcji monitor maszyny wirtualnej hosta z gościa operacyjnego i jego aplikacji. Aby uzyskać więcej informacji, wyszukaj dokumentu, "Intel Virtualization Technical Preview specyfikacji dla IA-32 architekturze firmy Intel," dokumentu numer C97063-002 w [Intel Corporation](https://software.intel.com/articles/intel-sdm) lokacji.

## <a name="requirements"></a>Wymagania

|Wewnętrzne|Architektura|
|---------------|------------------|
|`__vmx_vmlaunch`|X64|

**Plik nagłówkowy** \<intrin.h >

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz też

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)<br/>
[__vmx_vmresume](../intrinsics/vmx-vmresume.md)<br/>
[__vmx_vmclear](../intrinsics/vmx-vmclear.md)