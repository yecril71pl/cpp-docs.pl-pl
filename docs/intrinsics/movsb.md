---
title: __movsb | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: __movsb
dev_langs: C++
helpviewer_keywords:
- movsb instruction
- rep movsb instruction
- __movsb intrinsic
ms.assetid: ba5469f6-f797-4cd2-bee8-74c7666c26d4
caps.latest.revision: "15"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: d5ed046555b102c77b8213fc8755220d1f2d0777
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="movsb"></a>__movsb
**Dotyczące firmy Microsoft**  
  
 Generuje ciąg Przenieś (`rep movsb`) instrukcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
void __movsb(   
   unsigned char* Destination,   
   unsigned const char* Source,   
   size_t Count   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [out]`Destination`  
 Wskaźnik do miejsca docelowego kopii.  
  
 [in]`Source`  
 Wskaźnik do źródła kopii.  
  
 [in]`Count`  
 Liczba bajtów do skopiowania.  
  
## <a name="requirements"></a>Wymagania  
  
|— Wewnętrzne|Architektura|  
|---------------|------------------|  
|`__movsb`|x86,[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Plik nagłówka** \<intrin.h >  
  
## <a name="remarks"></a>Uwagi  
 W wyniku pierwszy `Count` bajtów wskazywana przez `Source` są kopiowane do `Destination` ciągu.  
  
 Ta procedura jest dostępna tylko wewnętrznie.  
  
## <a name="example"></a>Przykład  
  
```  
// movsb.cpp  
// processor: x86, x64  
#include <stdio.h>  
#include <intrin.h>  
  
#pragma intrinsic(__movsb)  
  
int main()  
{  
    unsigned char s1[100];  
    unsigned char s2[100] = "A big black dog.";  
    __movsb(s1, s2, 100);  
  
    printf_s("%s %s", s1, s2);  
}  
```  
  
```Output  
A big black dog. A big black dog.  
```  
  
**KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)