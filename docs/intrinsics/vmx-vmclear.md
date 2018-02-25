---
title: __vmx_vmclear | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- __vmx_vmclear
dev_langs:
- C++
helpviewer_keywords:
- VMCLEAR instruction
- __vmx_vmclear intrinsic
ms.assetid: e3eb98e4-50fc-4c93-9bac-340fd1f0a466
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 323fcf37ee9ecc9e62abe5d6fdc30944e58862f8
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="vmxvmclear"></a>__vmx_vmclear
**Microsoft Specific**  
  
 Inicjuje Struktura kontroli określonej maszyny wirtualnej (VMCS) i ustawia jego stan uruchomienia `Clear`.  
  
## <a name="syntax"></a>Składnia  
  
```  
unsigned char __vmx_vmclear(  
   unsigned __int64 *VmcsPhysicalAddress  
);  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|[in] `VmcsPhysicalAddress`|Wskaźnik do lokalizacji pamięci 64-bitowych, zawierający adres fizyczny VMCS, aby wyczyścić.|  
  
## <a name="return-value"></a>Wartość zwracana  
  
|Wartość|Znaczenie|  
|-----------|-------------|  
|0|Operacja zakończyła się pomyślnie.|  
|1|Operacja nie powiodła się ze stanem rozszerzonej dostępne w `VM-instruction error field` z bieżącym VMCS.|  
|2|Operacja nie powiodła się bez informacji o stanie.|  
  
## <a name="remarks"></a>Uwagi  
 Aplikację można wykonać operacji wprowadź maszyny Wirtualnej za pomocą [__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md) lub [__vmx_vmresume](../intrinsics/vmx-vmresume.md) funkcji. [__Vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md) funkcji można używać tylko z VMCS, ma stan uruchomienia `Clear`i [__vmx_vmresume](../intrinsics/vmx-vmresume.md) funkcji można używać tylko z VMCS, ma stan uruchomienia `Launched`. W związku z tym, użyj [__vmx_vmclear](../intrinsics/vmx-vmclear.md) funkcji, aby ustawić stan uruchomienia VMCS do `Clear`. Użyj [__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md) funkcji do pierwszej operacji wprowadź maszyny Wirtualnej i [__vmx_vmresume](../intrinsics/vmx-vmresume.md) funkcja dla kolejnych operacji wprowadź maszyny Wirtualnej.  
  
 `__vmx_vmclear` Funkcji jest odpowiednikiem `VMCLEAR` maszyny instrukcji. Ta funkcja obsługuje interakcji z hosta maszyny wirtualnej monitor Gość operacyjnego i jego zastosowań. Aby uzyskać więcej informacji, wyszukaj dokumentu "Intel Virtualization Technical specyfikacji dla IA-32 Intel architektury," dokumentu numer C97063-002 na [Intel Corporation](http://go.microsoft.com/fwlink/p/?linkid=127) lokacji.  
  
## <a name="requirements"></a>Wymagania  
  
|— Wewnętrzne|Architektura|  
|---------------|------------------|  
|`__vmx_vmclear`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Plik nagłówka** \<intrin.h >  
  
**KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)   
 [__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md)   
 [__vmx_vmresume](../intrinsics/vmx-vmresume.md)