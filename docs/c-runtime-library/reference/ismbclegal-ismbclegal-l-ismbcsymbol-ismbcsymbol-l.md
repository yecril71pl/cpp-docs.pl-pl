---
title: "_ismbclegal —, _ismbclegal_l —, _ismbcsymbol —, _ismbcsymbol_l — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _ismbclegal_l
- _ismbclegal
- _ismbcsymbol
- _ismbcsymbol_l
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-multibyte-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- ismbcsymbol_l
- _ismbcsymbol_l
- _ismbcsymbol
- _ismbclegal_l
- _ismbclegal
- ismbclegal_l
- ismbcsymbol
- ismbclegal
dev_langs: C++
helpviewer_keywords:
- ismbcsymbol function
- ismbclegal_l function
- _istlegal_l function
- istlegal function
- _istlegal function
- _ismbcsymbol function
- _ismbclegal_l function
- ismbclegal function
- ismbcsymbol_l function
- _ismbclegal function
- _ismbcsymbol_l function
- istlegal_l function
ms.assetid: 31bf1ea5-b56f-4e28-b21e-b49a2cf93ffc
caps.latest.revision: "18"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 057b6ee50934561662becbcf258910ee292664ef
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="ismbclegal-ismbclegall-ismbcsymbol-ismbcsymboll"></a>_ismbclegal, _ismbclegal_l, _ismbcsymbol, _ismbcsymbol_l
Sprawdza, czy znaków wielobajtowych prawnych lub znak symbolu.  
  
> [!IMPORTANT]
>  Nie można używać tego interfejsu API w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT, nie są obsługiwane z parametrem /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Składnia  
  
```  
int _ismbclegal(  
   unsigned int c   
);  
int _ismbclegal_l(  
   unsigned int c,   
   _locale_t locale  
);  
int _ismbcsymbol(  
   unsigned int c   
);  
int _ismbcsymbol_l(  
   unsigned int c,  
   _locale_t locale  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `c`  
 Znak do sprawdzenia.  
  
 `locale`  
 Ustawienia regionalne do użycia.  
  
## <a name="return-value"></a>Wartość zwracana  
 Każdy z tych procedur zwraca wartość różną od zera, jeśli znak spełnia warunek testu lub 0, jeśli jej nie ma. Jeśli `c`< = 255 i ma odpowiadającego `_ismbb` procedura (na przykład `_ismbcalnum` odpowiada `_ismbbalnum`), wynik jest zwracana wartość odpowiadającego `_ismbb` procedury.  
  
## <a name="remarks"></a>Uwagi  
 Każda z tych funkcji testy danego znaków wielobajtowych dla podanego warunku.  
  
 Wersje tych funkcji z `_l` sufiks są identyczne, z wyjątkiem tego, aby były używane ustawienia regionalne przekazana zamiast bieżące ustawienia regionalne dla ich działania zależnego od ustawień regionalnych. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).  
  
|Procedura|Stan testu|Przykład kodu strony 932|  
|-------------|--------------------|---------------------------|  
|`_ismbclegal`|Nieprawidłowa wielobajtowe|Zwraca wartość niezerową w przypadku i tylko wtedy, gdy pierwszy bajt `c` jest w zakresie 0x81-0x9F lub wartość 0xE0 - 0xFC, gdy drugi bajt znajduje się w zakresie 0x40-0x7E lub 0x80 - FC.|  
|`_ismbcsymbol`|Symbol wielobajtowe|Zwraca wartość niezerową w przypadku i tylko wtedy, gdy 0x8141 < =`c`< = 0x81AC.|  
  
### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu  
  
|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_istlegal`|Zawsze zwraca wartość false|`_ismbclegal`|Zawsze zwraca wartość false.|  
|`_istlegal_l`|Zawsze zwraca wartość false|`_ismbclegal_l`|Zawsze zwraca wartość false.|  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_ismbclegal,_ismbclegal_l`|\<mbstring.h >|  
|`_ismbcsymbol,_ismbcsymbol_l`|\<mbstring.h >|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Klasyfikacja znaków](../../c-runtime-library/character-classification.md)   
 [_ismbc — procedury](../../c-runtime-library/ismbc-routines.md)   
 [jest isw — procedury](../../c-runtime-library/is-isw-routines.md)   
 [_ismbb, procedury](../../c-runtime-library/ismbb-routines.md)