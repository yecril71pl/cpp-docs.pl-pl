---
title: __sidt | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __sidt
dev_langs:
- C++
helpviewer_keywords:
- sidt instruction
- __sidt intrinsic
ms.assetid: 01e83d14-6e63-4dea-8f64-5a0339d69641
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 96d20916210b0fe55817dceb86d388a33f8e238b
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/14/2018
ms.locfileid: "42465689"
---
# <a name="sidt"></a>__sidt
**Microsoft Specific**  
  
 Przechowuje wartość rejestru Tabela deskryptora przerwania (IDTR) w określonej lokalizacji pamięci.  
  
## <a name="syntax"></a>Składnia  
  
```  
void __sidt(  
     void *Destination);  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|[in] `Destination`|Wskaźnik do przechowywania IDTR lokalizacji w pamięci.|  
  
## <a name="requirements"></a>Wymagania  
  
|Wewnętrzne|Architektura|  
|---------------|------------------|  
|`__sidt`|x86, x64|  
  
 **Plik nagłówkowy** \<intrin.h >  
  
## <a name="remarks"></a>Uwagi  
 `__sidt` Funkcji jest odpowiednikiem `SIDT` machine instrukcji. Aby uzyskać więcej informacji, Wyszukaj w dokumencie "ręcznego deweloper oprogramowania architekturze firmy Intel, wolumin 2: odwołania do zestawu instrukcji," w [Intel Corporation](http://go.microsoft.com/fwlink/p/?linkid=127) lokacji.  
  
**END specyficzny dla Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)   
 [__lidt](../intrinsics/lidt.md)