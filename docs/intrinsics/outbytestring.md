---
title: __outbytestring | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 55dc6492faea101df40c2901ced24321822f36e8
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/14/2018
ms.locfileid: "42464747"
---
# <a name="outbytestring"></a>__outbytestring
**Microsoft Specific**  
  
 Generuje `rep outsb` instrukcji, która wysyła pierwszy `Count` bajtów danych wskazywanego przez `Buffer` port określony przez `Port`.  
  
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
 Dane, które zostaną wysłane do określonego portu.  
  
 [in] `Count`  
 Liczba bajtów danych do wysłania.  
  
## <a name="requirements"></a>Wymagania  
  
|Wewnętrzne|Architektura|  
|---------------|------------------|  
|`__outbytestring`|x86, x64|  
  
 **Plik nagłówkowy** \<intrin.h >  
  
## <a name="remarks"></a>Uwagi  
 Ta procedura jest dostępna wyłącznie jako wewnętrzna.  
  
**END specyficzny dla Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)