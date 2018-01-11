---
title: __vmx_vmptrst | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: __vmx_vmptrst
dev_langs: C++
helpviewer_keywords:
- __vmx_vmptrst intrinsic
- VMPTRST instruction
ms.assetid: 8dc66e47-03a0-41b0-8e25-c1485f42817a
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 176d8fe48e5719c345ab39135468edf324eeeaa5
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/03/2018
---
# <a name="vmxvmptrst"></a>__vmx_vmptrst
**Dotyczące firmy Microsoft**  
  
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
|`__vmx_vmptrst`|x86,[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Plik nagłówka** \<intrin.h >  
  
**KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)   
 [__vmx_vmptrld](../intrinsics/vmx-vmptrld.md)