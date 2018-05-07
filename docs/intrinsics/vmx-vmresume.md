---
title: __vmx_vmresume | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __vmx_vmresume
dev_langs:
- C++
helpviewer_keywords:
- __vmx_vmresume intrinsic
- VMRESUME instruction
ms.assetid: 233fe1b6-c727-493a-a484-1b2363732281
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8809489a71410af21e47d8771ec208340fc893a7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="vmxvmresume"></a>__vmx_vmresume
**Microsoft Specific**  
  
 Wznawia operacji inny niż główny VMX przy użyciu bieżącej struktury sterowania maszyny wirtualnej (VMCS).  
  
## <a name="syntax"></a>Składnia  
  
```  
unsigned char __vmx_vmresume(  
   void);  
```  
  
## <a name="return-value"></a>Wartość zwracana  
  
|Wartość|Znaczenie|  
|-----------|-------------|  
|0|Operacja zakończyła się pomyślnie.|  
|1|Operacja nie powiodła się ze stanem rozszerzonej dostępne w `VM-instruction error field` z bieżącym VMCS.|  
|2|Operacja nie powiodła się bez informacji o stanie.|  
  
## <a name="remarks"></a>Uwagi  
 Aplikację można wykonać operacji wprowadź maszyny Wirtualnej za pomocą [__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md) lub `__vmx_vmresume` funkcji. `__vmx_vmlaunch` Funkcji można używać tylko z VMCS, ma stan uruchomienia `Clear`i `__vmx_vmresume` funkcji można używać tylko z VMCS, ma stan uruchomienia `Launched`. W związku z tym, użyj [__vmx_vmclear](../intrinsics/vmx-vmclear.md) funkcji, aby ustawić stan uruchomienia VMCS do `Clear`, a następnie użyj `__vmx_vmlaunch` funkcji do pierwszej operacji wprowadź maszyny Wirtualnej i `__vmx_vmresume` funkcja dla kolejnych wprowadź maszyny Wirtualnej operacje.  
  
 `__vmx_vmresume` Funkcji jest odpowiednikiem `VMRESUME` maszyny instrukcji. Ta funkcja obsługuje interakcji z hosta maszyny wirtualnej monitor Gość operacyjnego i jego zastosowań. Aby uzyskać więcej informacji, wyszukaj dokumentu PDF "Intel Virtualization Technical specyfikacji dla IA-32 Intel architektury," dokumentu numer C97063-002 na [Intel Corporation](http://go.microsoft.com/fwlink/p/?linkid=127) lokacji.  
  
## <a name="requirements"></a>Wymagania  
  
|— Wewnętrzne|Architektura|  
|---------------|------------------|  
|`__vmx_vmresume`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Plik nagłówka** \<intrin.h >  
  
**KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)   
 [__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md)   
 [__vmx_vmclear](../intrinsics/vmx-vmclear.md)