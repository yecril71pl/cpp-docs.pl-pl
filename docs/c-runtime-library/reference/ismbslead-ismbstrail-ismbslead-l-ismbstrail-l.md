---
title: "_ismbslead —, _ismbstrail —, _ismbslead_l —, _ismbstrail_l — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _ismbstrail
- _ismbslead_l
- _ismbslead
- _ismbstrail_l
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
- _ismbslead
- ismbs
- ismbslead_l
- _ismbs
- ismbstrail_l
- ismbslead
- _ismbstrail
- _ismbstrail_l
- ismbstrail
- _ismbslead_l
dev_langs: C++
helpviewer_keywords:
- ismbstrail function
- _ismbslead function
- ismbslead function
- ismbslead_l function
- _ismbstrail function
- _ismbslead_l function
- ismbstrail_l function
- _ismbstrail_l function
ms.assetid: 86d2cd7a-3cff-443a-b713-14cc17a231e9
caps.latest.revision: "22"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: af774ccf790c258e1b0bc6bc5f8509eb4537607d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="ismbslead-ismbstrail-ismbsleadl-ismbstraill"></a>_ismbslead, _ismbstrail, _ismbslead_l, _ismbstrail_l
Wykonuje testy kontekstowa bajtów realizacji ciągu w przypadku znaków wielobajtowych i ślad bajtów i określa, czy wskaźnik danego podciągu wskazuje bajtu lub bajt.  
  
> [!IMPORTANT]
>  Nie można używać tego interfejsu API w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT, nie są obsługiwane z parametrem /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Składnia  
  
```  
int _ismbslead(  
   const unsigned char *str,  
   const unsigned char *current   
);  
int _ismbstrail(  
   const unsigned char *str,  
   const unsigned char *current   
);  
int _ismbslead_l(  
   const unsigned char *str,  
   const unsigned char *current,  
   _locale_t locale  
);  
int _ismbstrail_l(  
   const unsigned char *str,  
   const unsigned char *current,  
   _locale_t locale  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `str`  
 Wskaźnik do początku ciąg lub poprzednie znane bajtu.  
  
 `current`  
 Wskaźnik do pozycji w ciągu do sprawdzenia.  
  
 `locale`  
 Ustawienia regionalne do użycia.  
  
## <a name="return-value"></a>Wartość zwracana  
 `_ismbslead`Zwraca wartość -1, jeśli znak jest bajtu i `_ismbstrail` zwraca wartość -1, jeśli znak jest bajt. Jeśli parametry wejściowe są prawidłowe, ale nie są bajtu lub bajt, te funkcje zwracać zera. Jeśli którykolwiek argument ma `NULL`, program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, te funkcje zwracają `NULL` i ustaw `errno` do `EINVAL`.  
  
## <a name="remarks"></a>Uwagi  
 `_ismbslead`i `_ismbstrail` wolniej niż `_ismbblead` i `_ismbbtrail` wersji ponieważ uwzględniają kontekst ciągu.  
  
 Wersje tych funkcji, które mają `_l` sufiks są identyczne z tym, że ich działania zależnego od ustawień regionalnych używają ustawień regionalnych, który jest przekazywany w zamiast bieżące ustawienia regionalne. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|Opcjonalne nagłówki|  
|-------------|---------------------|---------------------|  
|`_ismbslead`|\<mbctype.h > lub \<mbstring.h >|\<CType.h >, * \<Limits.h — >, \<stdlib.h >|  
|`_ismbstrail`|\<mbctype.h > lub \<mbstring.h >|\<CType.h >, * \<Limits.h — >, \<stdlib.h >|  
|`_ismbslead_l`|\<mbctype.h > lub \<mbstring.h >|\<CType.h >, * \<Limits.h — >, \<stdlib.h >|  
|`_ismbstrail_l`|\<mbctype.h > lub \<mbstring.h >|\<CType.h >, * \<Limits.h — >, \<stdlib.h >|  
  
 \*Dla manifestu stałe warunki testu.  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Klasyfikacja znaków](../../c-runtime-library/character-classification.md)   
 [_ismbc — procedury](../../c-runtime-library/ismbc-routines.md)   
 [jest isw — procedury](../../c-runtime-library/is-isw-routines.md)   
 [_ismbb, procedury](../../c-runtime-library/ismbb-routines.md)