---
title: __vmx_vmread | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- __vmx_vmread
dev_langs:
- C++
helpviewer_keywords:
- VMREAD instruction
- __vmx_vmread intrinsic
ms.assetid: 08bdd7a0-6435-4ea6-b9a0-f592d870e5aa
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 351ef951a57a4f100861dbd12b8a77d11fc41df8
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="vmxvmread"></a>__vmx_vmread
**Microsoft Specific**  
  
 Odczytuje określone pole z bieżącej struktury sterowania maszyny wirtualnej (VMCS) i umieszcza je w określonej lokalizacji.  
  
## <a name="syntax"></a>Składnia  
  
```  
unsigned char __vmx_vmread(  
   size_t Field,  
   size_t *FieldValue  
);  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|[in] `Field`|Pole VMCS do odczytu.|  
|[in] `FieldValue`|Wskaźnik do lokalizację do przechowywania wartości odczytywać określone przez pole VMCS `Field` parametru.|  
  
## <a name="return-value"></a>Wartość zwracana  
  
|Wartość|Znaczenie|  
|-----------|-------------|  
|0|Operacja zakończyła się pomyślnie.|  
|1|Operacja nie powiodła się ze stanem rozszerzonej dostępne w `VM-instruction error field` z bieżącym VMCS.|  
|2|Operacja nie powiodła się bez informacji o stanie.|  
  
## <a name="remarks"></a>Uwagi  
 `__vmx_vmread` Funkcji jest odpowiednikiem `VMREAD` maszyny instrukcji. Wartość `Field` parametr jest zakodowany indeksu jest opisany w dokumentacji firmy Intel. Aby uzyskać więcej informacji, wyszukaj dokumentu "Intel Virtualization Technical specyfikacji dla IA-32 Intel architektury," dokumentu numer C97063-002 na [Intel Corporation](http://go.microsoft.com/fwlink/p/?linkid=127) lokacji, a następnie zapoznaj się dodatku C tego dokumentu .  
  
## <a name="requirements"></a>Wymagania  
  
|— Wewnętrzne|Architektura|  
|---------------|------------------|  
|`__vmx_vmread`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Plik nagłówka** \<intrin.h >  
  
**KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)   
 [__vmx_vmwrite](../intrinsics/vmx-vmwrite.md)