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
ms.workload: cplusplus
ms.openlocfilehash: e02bafc9319a6a3a4c5e07b46c9da6586f440d59
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/03/2018
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
  
 Ta funkcja obsługuje interakcji z hosta maszyny wirtualnej monitor Gość operacyjnego i jego zastosowań. Aby uzyskać więcej informacji, wyszukaj dokumentu, "wolumin ręczne AMD64 architektura programisty 2: programowania w języku systemu," numer 24593, poprawki 3.11, dokumentu w [AMD corporation](http://go.microsoft.com/fwlink/p/?linkid=23746) lokacji.  
  
## <a name="requirements"></a>Wymagania  
  
|— Wewnętrzne|Architektura|  
|---------------|------------------|  
|`__svm_skinit`|x86,[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Plik nagłówka** \<intrin.h >  
  
**KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)