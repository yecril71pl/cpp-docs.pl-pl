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
ms.openlocfilehash: 3ff43920400028e0fb13fc17615fb58cc551726b
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45704226"
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
*Port*<br/>
[in] Port do wysyłania danych do.  
  
*Bufor*<br/>
[in] Wskaźnik do danych, które zostaną wysłane do określonego portu.  
  
*Liczba*<br/>
[in] Liczba wyrazy w liczbie mnogiej do wysłania.  
  
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