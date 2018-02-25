---
title: __inwordstring | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- __inwordstring
- __inwordstring_cpp
dev_langs:
- C++
helpviewer_keywords:
- __inwordstring intrinsic
- rep insw instruction
ms.assetid: 6de37939-017a-4740-9e3d-7de78a30daba
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7690ae817961e268ee004d03beef453502880009
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="inwordstring"></a>__inwordstring
**Microsoft Specific**  
  
 Odczytuje dane z określonego portu przy użyciu `rep insw` instrukcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
void __inwordstring(  
   unsigned short Port,  
   unsigned short* Buffer,  
   unsigned long Count  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [in] `Port`  
 Port do odczytu.  
  
 [out] `Buffer`  
 Dane odczytywane z portu są zapisywane w tym miejscu.  
  
 [in] `Count`  
 Liczba słów dane do odczytu.  
  
## <a name="requirements"></a>Wymagania  
  
|— Wewnętrzne|Architektura|  
|---------------|------------------|  
|`__inwordstring`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Plik nagłówka** \<intrin.h >  
  
## <a name="remarks"></a>Uwagi  
 Ta procedura jest dostępna tylko wewnętrznie.  
  
**KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)