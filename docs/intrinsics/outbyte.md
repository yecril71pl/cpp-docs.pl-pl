---
title: __outbyte | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: __outbyte
dev_langs: C++
helpviewer_keywords:
- out instruction
- __outbyte intrinsic
ms.assetid: c4cd1a34-8a02-4e37-993d-3201bc17901a
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 76d162bd3052ddf1516af6650b45f33c6b348c02
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="outbyte"></a>__outbyte
**Dotyczące firmy Microsoft**  
  
 Generuje `out` instrukcji, który wysyła 1 bajt, określony przez `Data` z portu We/Wy, określony przez `Port`.  
  
## <a name="syntax"></a>Składnia  
  
```  
void __outbyte(   
   unsigned short Port,   
   unsigned char Data   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [in]`Port`  
 Port do wysyłania danych do.  
  
 [in]`Data`  
 Bajtów do wysłania określonego portu.  
  
## <a name="requirements"></a>Wymagania  
  
|— Wewnętrzne|Architektura|  
|---------------|------------------|  
|`__outbyte`|x86,[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Plik nagłówka** \<intrin.h >  
  
## <a name="remarks"></a>Uwagi  
 Ta procedura jest dostępna tylko wewnętrznie.  
  
**KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)