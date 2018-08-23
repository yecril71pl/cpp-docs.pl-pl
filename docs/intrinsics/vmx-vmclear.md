---
title: __vmx_vmclear | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __vmx_vmclear
dev_langs:
- C++
helpviewer_keywords:
- VMCLEAR instruction
- __vmx_vmclear intrinsic
ms.assetid: e3eb98e4-50fc-4c93-9bac-340fd1f0a466
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7d93cff5c1be0847a6c88f0d60b89527388e4d8b
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/14/2018
ms.locfileid: "42466438"
---
# <a name="vmxvmclear"></a>__vmx_vmclear
**Microsoft Specific**  
  
 Inicjuje struktury sterowania określonej maszyny wirtualnej (VMCS) i ustawia jego stan uruchomienia `Clear`.  
  
## <a name="syntax"></a>Składnia  
  
```  
unsigned char __vmx_vmclear(  
   unsigned __int64 *VmcsPhysicalAddress  
);  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|[in] `VmcsPhysicalAddress`|Wskaźnik do lokalizacji pamięci 64-bitowych, która zawiera adres fizyczny VMCS do wyczyszczenia.|  
  
## <a name="return-value"></a>Wartość zwracana  
  
|Wartość|Znaczenie|  
|-----------|-------------|  
|0|Operacja zakończyła się pomyślnie.|  
|1|Operacja nie powiodła się z rozszerzonych informacji o stanie w `VM-instruction error field` z bieżącym VMCS.|  
|2|Operacja nie powiodła się bez informacji o stanie.|  
  
## <a name="remarks"></a>Uwagi  
 Aplikacja może wykonywać operację wprowadź maszyny Wirtualnej przy użyciu [__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md) lub [__vmx_vmresume](../intrinsics/vmx-vmresume.md) funkcji. [__Vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md) funkcji można używać tylko w przypadku VMCS, ma stan uruchomienia `Clear`i [__vmx_vmresume](../intrinsics/vmx-vmresume.md) funkcji można używać tylko w przypadku VMCS, ma stan uruchomienia `Launched`. W związku z tym, użyj [__vmx_vmclear](../intrinsics/vmx-vmclear.md) funkcję, aby ustawić stan uruchomienia VMCS do `Clear`. Użyj [__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md) funkcji do pierwszej operacji maszyny Wirtualnej, wprowadź i [__vmx_vmresume](../intrinsics/vmx-vmresume.md) funkcji dla kolejnych operacji wprowadź maszyny Wirtualnej.  
  
 `__vmx_vmclear` Funkcji jest odpowiednikiem `VMCLEAR` machine instrukcji. Ta funkcja obsługuje interakcji monitor maszyny wirtualnej hosta z gościa operacyjnego i jego aplikacji. Aby uzyskać więcej informacji, wyszukaj dokumentu, "Intel Virtualization Technical Preview specyfikacji dla IA-32 architekturze firmy Intel," dokumentu numer C97063-002 w [Intel Corporation](http://go.microsoft.com/fwlink/p/?linkid=127) lokacji.  
  
## <a name="requirements"></a>Wymagania  
  
|Wewnętrzne|Architektura|  
|---------------|------------------|  
|`__vmx_vmclear`|X64|  
  
 **Plik nagłówkowy** \<intrin.h >  
  
**END specyficzny dla Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)   
 [__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md)   
 [__vmx_vmresume](../intrinsics/vmx-vmresume.md)