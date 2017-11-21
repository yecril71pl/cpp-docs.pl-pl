---
title: __svm_skinit | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: __svm_skinit
dev_langs: C++
helpviewer_keywords:
- SKINIT instruction
- __svm_skinit intrinsic
ms.assetid: 787ec781-4cf2-40a2-aa20-5192334b131a
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 63f58bed44dcea47c925f94b90e9438eb1082962
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="svmskinit"></a>__svm_skinit
**Dotyczące firmy Microsoft**  
  
 Inicjuje ładowanie sprawdzalnie bezpieczny oprogramowania, np. monitor maszyny wirtualnej.  
  
## <a name="syntax"></a>Składnia  
  
```  
void __svm_skinit(  
   int SLB  
);  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`SLB`|32-bitowy adres fizyczny bajtów 64K Secure modułu ładującego bloku Programowego.|  
  
## <a name="remarks"></a>Uwagi  
 `__svm_skinit` Funkcji jest odpowiednikiem `SKINIT` maszyny instrukcji. Ta funkcja jest częścią systemu zabezpieczeń, które korzysta z procesora i zaufanych Platform Module (TPM) aby zweryfikować i załadować zaufanego oprogramowania o nazwie jądra zabezpieczeń (SK). Monitor maszyny wirtualnej jest przykładem jądra zabezpieczeń. System zabezpieczeń sprawdza, składniki programu załadowany podczas procesu inicjowania i chroni przed naruszeniami poprzez przerwań, dostęp do urządzeń lub innego programu, jeśli komputer jest wieloprocesorowych składników.  
  
 `SLB` Parametr określa adres fizyczny bloku 64 KB pamięci o nazwie *Secure bloku modułu ładującego* (Programowego). Programowego zawiera program o nazwie bezpiecznego modułu ładującego, ustanawia środowisku operacyjnym dla komputera, a następnie ładuje jądra zabezpieczeń.  
  
 Ta funkcja obsługuje interakcji z hosta maszyny wirtualnej monitor Gość operacyjnego i jego zastosowań. Aby uzyskać więcej informacji, wyszukaj dokumentu, "wolumin ręczne AMD64 architektura programisty 2: programowania w języku systemu," numer 24593, poprawki 3.11, dokumentu w [AMD corporation](http://go.microsoft.com/fwlink/?LinkId=23746) lokacji.  
  
## <a name="requirements"></a>Wymagania  
  
|— Wewnętrzne|Architektura|  
|---------------|------------------|  
|`__svm_skinit`|x86,[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Plik nagłówka** \<intrin.h >  
  
**KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)