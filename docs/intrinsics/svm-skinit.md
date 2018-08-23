---
title: __svm_skinit | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __svm_skinit
dev_langs:
- C++
helpviewer_keywords:
- SKINIT instruction
- __svm_skinit intrinsic
ms.assetid: 787ec781-4cf2-40a2-aa20-5192334b131a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d0912b7a1ff41bf7a21da198268dbd4b8dc920a9
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/14/2018
ms.locfileid: "42465056"
---
# <a name="svmskinit"></a>__svm_skinit
**Microsoft Specific**  
  
 Inicjuje ładowanie i bezpiecznego oprogramowania, np. monitor maszyny wirtualnej.  
  
## <a name="syntax"></a>Składnia  
  
```  
void __svm_skinit(  
   int SLB  
);  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`SLB`|32-bitowy adres fizyczny bajt 64K zabezpieczanie modułu ładującego bloku (SLB).|  
  
## <a name="remarks"></a>Uwagi  
 `__svm_skinit` Funkcji jest odpowiednikiem `SKINIT` machine instrukcji. Ta funkcja jest częścią system zabezpieczeń, który korzysta z procesora i zaufanych Platform Module (TPM) w celu sprawdzenia i załadować zaufane oprogramowanie o nazwie jądra zabezpieczeń (SK). Monitorowanie maszyny wirtualnej znajduje się przykład jądra zabezpieczeń. System zabezpieczeń sprawdza, składniki programu załadowany w procesie inicjowania i chroni składników przed naruszeniami poprzez przerwań, uzyskiwania dostępu do urządzenia lub innego programu, jeśli komputer jest wieloprocesorowych.  
  
 `SLB` Parametr określa adres fizyczny bloku 64 KB pamięci o nazwie *zabezpieczanie modułu ładującego bloku* (SLB). SLB zawiera program o nazwie bezpiecznego modułu ładującego, która ustanawia środowisko operacyjne dla komputera, a następnie ładuje jądra zabezpieczeń.  
  
 Ta funkcja obsługuje interakcji monitor maszyny wirtualnej hosta z gościa operacyjnego i jego aplikacji. Aby uzyskać więcej informacji, wyszukaj dokumentu, "AMD64 architektury programisty ręczne woluminie 2: programowania systemu" numer 24593, wersji 3.11, dokumentu w [AMD corporation](http://go.microsoft.com/fwlink/p/?linkid=23746) lokacji.  
  
## <a name="requirements"></a>Wymagania  
  
|Wewnętrzne|Architektura|  
|---------------|------------------|  
|`__svm_skinit`|x86, x64|  
  
 **Plik nagłówkowy** \<intrin.h >  
  
**END specyficzny dla Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)