---
title: __outdwordstring | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __outdwordstring
dev_langs:
- C++
helpviewer_keywords:
- outsd instruction
- __outdwordstring intrinsic
- rep outsd instruction
ms.assetid: 55b31a65-aab7-4b5c-b61d-d9e2fb0c497a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: adc104e3325a2a9fda922f8ef32aa84982f35366
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/14/2018
ms.locfileid: "42464654"
---
# <a name="outdwordstring"></a>__outdwordstring
**Microsoft Specific**  
  
 Generuje `rep outsd` instrukcji, która wysyła `Count` wyrazy w liczbie mnogiej zaczynając od `Buffer` z portu We/Wy, określony przez `Port`.  
  
## <a name="syntax"></a>Składnia  
  
```  
void __outdwordstring(   
   unsigned short Port,   
   unsigned long* Buffer,   
   unsigned long Count   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [in] `Port`  
 Port do wysyłania danych do.  
  
 [in] `Buffer`  
 Wskaźnik do danych, które zostaną wysłane do określonego portu.  
  
 [in] `Count`  
 Liczba wyrazy w liczbie mnogiej do wysłania.  
  
## <a name="requirements"></a>Wymagania  
  
|Wewnętrzne|Architektura|  
|---------------|------------------|  
|`__outdwordstring`|x86, x64|  
  
 **Plik nagłówkowy** \<intrin.h >  
  
## <a name="remarks"></a>Uwagi  
 Ta procedura jest dostępna wyłącznie jako wewnętrzna.  
  
**END specyficzny dla Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)