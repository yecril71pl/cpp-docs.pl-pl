---
title: __vmx_vmwrite | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __vmx_vmwrite
dev_langs:
- C++
helpviewer_keywords:
- __vmx_vmwrite intrinsic
- VMWRITE instruction
ms.assetid: 88139792-fd3f-4210-97ca-9d84f43a0252
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 132841c8c24e2b625dad218aaaef2a19cba0a264
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43680501"
---
# <a name="vmxvmwrite"></a>__vmx_vmwrite
**Microsoft Specific**  
  
 Zapisuje określoną wartość określonego pola w strukturze kontroli bieżącej maszyny wirtualnej (VMCS).  
  
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
|[in] `Field`|Pole VMCS do zapisania.|  
|[in] `FieldValue`|Wartość do zapisania się do pola VMCS.|  
  
## <a name="return-value"></a>Wartość zwracana  
 0  
 Operacja zakończyła się pomyślnie.  
  
 1  
 Operacja nie powiodła się z rozszerzonych informacji o stanie w `VM-instruction error field` z bieżącym VMCS.  
  
 2  
 Operacja nie powiodła się bez informacji o stanie.  
  
## <a name="remarks"></a>Uwagi  
 `__vmx_vmwrite` Funkcji jest odpowiednikiem `VMWRITE` machine instrukcji. Wartość `Field` parametr jest zakodowany indeksu jest opisane w dokumentacji firmy Intel. Aby uzyskać więcej informacji, wyszukaj dokumentu, "Intel Virtualization Technical Preview specyfikacji dla IA-32 architekturze firmy Intel," dokumentu numer C97063-002 w [Intel Corporation](https://software.intel.com/en-us/articles/intel-sdm) lokacji, a następnie zapoznaj się z dodatku C dokument.  
  
## <a name="requirements"></a>Wymagania  
  
|Wewnętrzne|Architektura|  
|---------------|------------------|  
|`__vmx_vmwrite`|X64|  
  
 **Plik nagłówkowy** \<intrin.h >  
  
**END specyficzny dla Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)   
 [__vmx_vmread](../intrinsics/vmx-vmread.md)