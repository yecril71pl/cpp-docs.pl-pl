---
title: __inbyte | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- __inbyte
- __inbyte_cpp
dev_langs:
- C++
helpviewer_keywords:
- in instruction
- __inbyte intrinsic
ms.assetid: 03b61799-2a08-474d-adc4-2cbf7c81a4d5
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c3acb6e5a5fc5f9f9a6808ae8b2047da32b1b2d4
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="inbyte"></a>__inbyte
**Microsoft Specific**  
  
 Generuje `in` instrukcji, zwracając jednego bajtu odczytywać określony przez port `Port`.  
  
## <a name="syntax"></a>Składnia  
  
```  
unsigned char __inbyte(  
   unsigned short Port  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [in] `Port`  
 Port do odczytu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Bajtów odczytanych z określonego portu.  
  
## <a name="requirements"></a>Wymagania  
  
|— Wewnętrzne|Architektura|  
|---------------|------------------|  
|`__inbyte`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Plik nagłówka** \<intrin.h >  
  
**KOŃCOWY określonych firmy Microsoft**  
  
## <a name="remarks"></a>Uwagi  
 Ta procedura jest dostępna tylko wewnętrznie.  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)