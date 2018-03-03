---
title: Mapowanie typu danych | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _TXCHAR
- _TUCHAR
- _TINT
- _TSCHAR
- _TCHAR
- TCHAR::H
- TCHAR
- _T
- _TEXT
dev_langs:
- C++
helpviewer_keywords:
- _TXCHAR type
- TINT type
- _TCHAR type
- TSCHAR type
- TEXT type
- TCHAR type
- TCHAR.H data types, mappings defined in
- generic-text data types
- _TINT type
- TUCHAR type
- TXCHAR type
- _TSCHAR type
- T type
- _TUCHAR type
- _TEXT type
- _T type
ms.assetid: 4e573c05-8800-468b-ae5f-76ff7409835e
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f52c6e5664292469ef33a88e9d5458c07ec69454
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="data-type-mappings"></a>Mapowanie typu danych
Te mapowania typu danych są definiowane w tchar —. H i zależą od tego, czy stała `_UNICODE` lub `_MBCS` został zdefiniowany w programie.  
  
 Aby uzyskać odpowiednie informacje, zobacz [przy użyciu tchar —. Typy danych H z kodem _MBCS](../text/using-tchar-h-data-types-with-mbcs-code.md).  
  
### <a name="generic-text-data-type-mappings"></a>Mapowanie typu danych — zwykły tekst  
  
|Zwykły tekst<br /><br /> Nazwa typu danych|SBCS (_UNICODE —,<br /><br /> _MBCS nie<br /><br /> zdefiniowana)|_MBCS<br /><br /> zdefiniowane|_UNICODE —<br /><br /> zdefiniowane|  
|--------------------------------------|----------------------------------------------------|------------------------|---------------------------|  
|`_TCHAR`|`char`|`char`|`wchar_t`|  
|`_tfinddata_t`|`_finddata_t`|`_finddata_t`|`_wfinddata_t`|  
|`_tfinddata64_t`|`__finddata64_t`|`__finddata64_t`|`__wfinddata64_t`|  
|`_tfinddatai64_t`|`_finddatai64_t`|`_finddatai64_t`|`_wfinddatai64_t`|  
|`_TINT`|`int`|`int`|`wint_t`|  
|`_TSCHAR`|`signed char`|`signed char`|`wchar_t`|  
|`_TUCHAR`|`unsigned char`|`unsigned char`|`wchar_t`|  
|`_TXCHAR`|`char`|`unsigned char`|`wchar_t`|  
|`_T`lub`_TEXT`|Żadnego skutku (usuwane przez preprocesora)|Żadnego skutku (usuwane przez preprocesora)|`L`(konwertuje zgodnie z jego odpowiednikiem Unicode znak lub ciąg)|  
  
## <a name="see-also"></a>Zobacz też  
 [Mapowania zwykłego tekstu](../c-runtime-library/generic-text-mappings.md)   
 [Mapowania zmiennych globalnych i stałych](../c-runtime-library/constant-and-global-variable-mappings.md)   
 [Mapowanie procedur](../c-runtime-library/routine-mappings.md)   
 [Przykładowy ogólny Program tekstowy](../c-runtime-library/a-sample-generic-text-program.md)   
 [Mapowania zwykłego tekstu](../c-runtime-library/using-generic-text-mappings.md)