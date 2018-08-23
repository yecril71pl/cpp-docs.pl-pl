---
title: __indwordstring | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __indwordstring
- __indwordstring_cpp
dev_langs:
- C++
helpviewer_keywords:
- __indwordstring intrinsic
- rep insd instruction
ms.assetid: 96a1cf33-f691-4916-99e4-fa849b61e3a9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 00c0f8e67a535d126eab3a19bf17b0bf8bfd7440
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/14/2018
ms.locfileid: "42466235"
---
# <a name="indwordstring"></a>__indwordstring
**Microsoft Specific**  
  
 Odczytuje dane z określonego portu przy użyciu `rep insd` instrukcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
void __indwordstring(  
   unsigned short Port,  
   unsigned long* Buffer,  
   unsigned long Count  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [in] `Port`  
 Port do odczytu.  
  
 [out] `Buffer`  
 Dane odczytywane z portu są zapisywane w tym miejscu.  
  
 [in] `Count`  
 Liczba bajtów danych do odczytu.  
  
## <a name="requirements"></a>Wymagania  
  
|Wewnętrzne|Architektura|  
|---------------|------------------|  
|`__indwordstring`|x86, x64|  
  
 **Plik nagłówkowy** \<intrin.h >  
  
## <a name="remarks"></a>Uwagi  
 Ta procedura jest dostępna wyłącznie jako wewnętrzna.  
  
**END specyficzny dla Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)