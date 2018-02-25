---
title: __outdword | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- __outdword
dev_langs:
- C++
helpviewer_keywords:
- out instruction
- outdword instruction
- __outdword intrinsic
ms.assetid: ed1e4994-a84b-4759-8bf9-cd48fb073f4d
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: aefad542b6fa3f1567684edc23c13548496ce37f
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="outdword"></a>__outdword
**Microsoft Specific**  
  
 Generuje `out` instrukcji można wysłać z bitowego `Data` z portu `Port`.  
  
## <a name="syntax"></a>Składnia  
  
```  
void __outdword(   
   unsigned short Port,   
   unsigned long Data   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [in] `Port`  
 Port do wysyłania danych do.  
  
 [in] `Data`  
 Bitowego do wysłania.  
  
## <a name="requirements"></a>Wymagania  
  
|— Wewnętrzne|Architektura|  
|---------------|------------------|  
|`__outdword`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Plik nagłówka** \<intrin.h >  
  
## <a name="remarks"></a>Uwagi  
 Ta procedura jest dostępna tylko wewnętrznie.  
  
**KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)