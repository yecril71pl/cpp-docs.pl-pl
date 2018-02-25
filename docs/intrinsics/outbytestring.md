---
title: __outbytestring | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- __outbytestring
dev_langs:
- C++
helpviewer_keywords:
- rep outsb instruction
- __outbytestring intrinsic
- outsb instruction
ms.assetid: c9150661-9c18-427f-bae8-710bba6ed78c
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 731d31e8b06b999cede64d550ad52382bc432bb8
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="outbytestring"></a>__outbytestring
**Microsoft Specific**  
  
 Generuje `rep outsb` instrukcji, która wysyła pierwszy `Count` bajtów danych wskazywanego przez `Buffer` z portem określonym przez `Port`.  
  
## <a name="syntax"></a>Składnia  
  
```  
void __outbytestring(   
   unsigned short Port,   
   unsigned char* Buffer,   
   unsigned long Count   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [in] `Port`  
 Port do wysyłania danych do.  
  
 [in] `Buffer`  
 Dane mają być wysyłane z określonego portu.  
  
 [in] `Count`  
 Liczba bajtów danych do wysłania.  
  
## <a name="requirements"></a>Wymagania  
  
|— Wewnętrzne|Architektura|  
|---------------|------------------|  
|`__outbytestring`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Plik nagłówka** \<intrin.h >  
  
## <a name="remarks"></a>Uwagi  
 Ta procedura jest dostępna tylko wewnętrznie.  
  
**KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)