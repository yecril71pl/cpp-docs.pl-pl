---
title: __vmx_vmwrite | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- __vmx_vmwrite
dev_langs:
- C++
helpviewer_keywords:
- __vmx_vmwrite intrinsic
- VMWRITE instruction
ms.assetid: 88139792-fd3f-4210-97ca-9d84f43a0252
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 08cd68256e1219df36ce6f9ea22165938fba44af
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="vmxvmwrite"></a>__vmx_vmwrite
**Microsoft Specific**  
  
 Zapisuje określoną wartość określonego pola w bieżącym Struktura kontroli maszyny wirtualnej (VMCS).  
  
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
|[in] `Field`|Pole VMCS do zapisu.|  
|[in] `FieldValue`|Wartość do zapisania do pola VMCS.|  
  
## <a name="return-value"></a>Wartość zwracana  
 0  
 Operacja zakończyła się pomyślnie.  
  
 1  
 Operacja nie powiodła się ze stanem rozszerzonej dostępne w `VM-instruction error field` z bieżącym VMCS.  
  
 2  
 Operacja nie powiodła się bez informacji o stanie.  
  
## <a name="remarks"></a>Uwagi  
 `__vmx_vmwrite` Funkcji jest odpowiednikiem `VMWRITE` maszyny instrukcji. Wartość `Field` parametr jest zakodowany indeksu jest opisany w dokumentacji firmy Intel. Aby uzyskać więcej informacji, wyszukaj dokumentu "Intel Virtualization Technical specyfikacji dla IA-32 Intel architektury," dokumentu numer C97063-002 na [Intel Corporation](http://go.microsoft.com/fwlink/p/?linkid=127) lokacji i zapoznaj się dodatku C dokument.  
  
## <a name="requirements"></a>Wymagania  
  
|— Wewnętrzne|Architektura|  
|---------------|------------------|  
|`__vmx_vmwrite`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Plik nagłówka** \<intrin.h >  
  
**KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)   
 [__vmx_vmread](../intrinsics/vmx-vmread.md)