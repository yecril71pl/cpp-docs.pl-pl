---
title: __vmx_vmptrst | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- __vmx_vmptrst
dev_langs:
- C++
helpviewer_keywords:
- __vmx_vmptrst intrinsic
- VMPTRST instruction
ms.assetid: 8dc66e47-03a0-41b0-8e25-c1485f42817a
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a08626cd6238df51ee149cc7bf8d873b993fb95e
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="vmxvmptrst"></a>__vmx_vmptrst
**Microsoft Specific**  
  
 Przechowuje wskaźnik do bieżącej struktury kontroli maszyn wirtualnych (VMCS) pod określonym adresem.  
  
## <a name="syntax"></a>Składnia  
  
```  
void __vmx_vmptrst(   
   unsigned __int64 *VmcsPhysicalAddress   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [w] *`VmcsPhysicalAddress`  
 Adres przechowywania bieżącego wskaźnika VMCS.  
  
## <a name="remarks"></a>Uwagi  
 Wskaźnik VMCS jest 64-bitowy adres fizyczny.  
  
 `__vmx_vmptrst` Funkcji jest odpowiednikiem `VMPTRST` maszyny instrukcji. Ta funkcja obsługuje interakcji z hosta maszyny wirtualnej monitor Gość operacyjnego i jego zastosowań. Aby uzyskać więcej informacji, wyszukaj dokumentu "Intel Virtualization Technical specyfikacji dla IA-32 Intel architektury," dokumentu numer C97063-002 na [Intel Corporation](http://go.microsoft.com/fwlink/p/?linkid=127) lokacji.  
  
## <a name="requirements"></a>Wymagania  
  
|— Wewnętrzne|Architektura|  
|---------------|------------------|  
|`__vmx_vmptrst`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Plik nagłówka** \<intrin.h >  
  
**KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)   
 [__vmx_vmptrld](../intrinsics/vmx-vmptrld.md)