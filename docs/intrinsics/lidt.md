---
title: __lidt | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __lidt
- __lidt_cpp
dev_langs:
- C++
helpviewer_keywords:
- LIDT instruction
- __lidt intrinsic
ms.assetid: 8298d25d-a19e-4900-828d-6b3b09841882
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f6f73e37c8fddc54e91be13d83c54f126ab6b5a0
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/14/2018
ms.locfileid: "42466139"
---
# <a name="lidt"></a>__lidt
**Microsoft Specific**  
  
 Ładuje deskryptora tabeli Rejestr przerwań (IDTR) z wartością w określonej lokalizacji pamięci.  
  
## <a name="syntax"></a>Składnia  
  
```  
void __lidt(  
     void *Source);  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|[in] `Source`|Wskaźnik do wartości, które mają być kopiowane do IDTR.|  
  
## <a name="requirements"></a>Wymagania  
  
|Wewnętrzne|Architektura|  
|---------------|------------------|  
|`__lidt`|x86, x64|  
  
 **Plik nagłówkowy** \<intrin.h >  
  
## <a name="remarks"></a>Uwagi  
 `__lidt` Funkcji jest odpowiednikiem `LIDT` komputera instrukcji i jest dostępna tylko w trybie jądra. Aby uzyskać więcej informacji, Wyszukaj w dokumencie "ręcznego deweloper oprogramowania architekturze firmy Intel, wolumin 2: odwołania do zestawu instrukcji," w [Intel Corporation](http://go.microsoft.com/fwlink/p/?linkid=127) lokacji.  
  
**END specyficzny dla Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)   
 [__sidt](../intrinsics/sidt.md)