---
title: __vmx_vmread | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __vmx_vmread
dev_langs:
- C++
helpviewer_keywords:
- VMREAD instruction
- __vmx_vmread intrinsic
ms.assetid: 08bdd7a0-6435-4ea6-b9a0-f592d870e5aa
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c0c8b5a22cfef8ebde74fbe6d1f6920a969e7bc6
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45706384"
---
# <a name="vmxvmread"></a>__vmx_vmread
**Microsoft Specific**  
  
 Odczytuje określone pole od bieżącej struktury sterowania maszyny wirtualnej (VMCS) i umieszcza je w określonej lokalizacji.  
  
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
|*Pole*|[in] Pole VMCS do odczytu.|  
|*Wartość FieldValue*|[in] Wskaźnik do lokalizacji, do przechowywania wartości odczytywać określone przez pole VMCS `Field` parametru.|  
  
## <a name="return-value"></a>Wartość zwracana  
  
|Wartość|Znaczenie|  
|-----------|-------------|  
|0|Operacja zakończyła się pomyślnie.|  
|1|Operacja nie powiodła się z rozszerzonych informacji o stanie w `VM-instruction error field` z bieżącym VMCS.|  
|2|Operacja nie powiodła się bez informacji o stanie.|  
  
## <a name="remarks"></a>Uwagi  
 `__vmx_vmread` Funkcji jest odpowiednikiem `VMREAD` machine instrukcji. Wartość `Field` parametr jest zakodowany indeksu jest opisane w dokumentacji firmy Intel. Aby uzyskać więcej informacji, wyszukaj dokumentu, "Intel Virtualization Technical Preview specyfikacji dla IA-32 architekturze firmy Intel," dokumentu numer C97063-002 w [Intel Corporation](https://software.intel.com/en-us/articles/intel-sdm) lokacji, a następnie zapoznaj się z dodatku C tego dokumentu .  
  
## <a name="requirements"></a>Wymagania  
  
|Wewnętrzne|Architektura|  
|---------------|------------------|  
|`__vmx_vmread`|X64|  
  
 **Plik nagłówkowy** \<intrin.h >  
  
**END specyficzny dla Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)   
 [__vmx_vmwrite](../intrinsics/vmx-vmwrite.md)