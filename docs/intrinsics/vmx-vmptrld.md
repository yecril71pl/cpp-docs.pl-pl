---
title: __vmx_vmptrld | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: __vmx_vmptrld
dev_langs: C++
helpviewer_keywords:
- __vmx_vmptrld intrinsic
- VMPTRLD instruction
ms.assetid: 95c9ec5b-1a81-41ba-983e-327bd6a65fcb
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 6491eb24b8ed615d6309f81ceb0770ba0973d79b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="vmxvmptrld"></a>__vmx_vmptrld
**Dotyczące firmy Microsoft**  
  
 Ładuje wskaźnik do bieżącej struktury kontroli maszyn wirtualnych (VMCS) z określonego adresu.  
  
## <a name="syntax"></a>Składnia  
  
```  
int __vmx_vmptrld(   
   unsigned __int64 *VmcsPhysicalAddress   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [w] *`VmcsPhysicalAddress`  
 Adres, gdzie znajduje się wskaźnik VMCS.  
  
## <a name="return-value"></a>Wartość zwracana  
 0  
 Operacja zakończyła się pomyślnie.  
  
 1  
 Operacja nie powiodła się ze stanem rozszerzonej dostępne w `VM-instruction error field` z bieżącym VMCS.  
  
 2  
 Operacja nie powiodła się bez informacji o stanie.  
  
## <a name="remarks"></a>Uwagi  
 Wskaźnik VMCS jest 64-bitowy adres fizyczny.  
  
 `__vmx_vmptrld` Funkcji jest odpowiednikiem `VMPTRLD` maszyny instrukcji. Ta funkcja obsługuje interakcji z hosta maszyny wirtualnej monitor Gość operacyjnego i jego zastosowań. Aby uzyskać więcej informacji, wyszukaj dokumentu "Intel Virtualization Technical specyfikacji dla IA-32 Intel architektury," dokumentu numer C97063-002 na [Intel Corporation](http://go.microsoft.com/fwlink/?LinkId=127) lokacji.  
  
## <a name="requirements"></a>Wymagania  
  
|— Wewnętrzne|Architektura|  
|---------------|------------------|  
|`__vmx_vmptrld`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Plik nagłówka** \<intrin.h >  
  
**KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)   
 [__vmx_vmptrst](../intrinsics/vmx-vmptrst.md)