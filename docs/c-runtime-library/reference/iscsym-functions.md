---
title: "iscsym —, iscsymf —, __iscsym —, __iswcsym —, __iscsymf —, __iswcsymf —, _iscsym_l —, _iswcsym_l —, _iscsymf_l —, _iswcsymf_l — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _iswcsym_l
- __iswcsym
- __iscsym
- _iswcsymf_l
- _iscsym_l
- __iswcsymf
- __iscsymf
- _iscsymf_l
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
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _iswcsym_l
- _iswcsymf_l
- iscsymf
- iswcsymf
- __iswcsym
- __iswcsymf
- iscsym
- iswcsym
- __iscsym
- _iscsym_l
- _iscsymf_l
- __iscsymf
- ctype/iscsym
- ctype/iscsymf
- ctype/__iscsym
- ctype/__iscsymf
- ctype/__iscsym_l
- ctype/__iscsymf_l
- ctype/__iswcsym
- ctype/__iswcsymf
- ctype/__iswcsym_l
- ctype/__iswcsymf_l
dev_langs: C++
helpviewer_keywords:
- iscsymf_l function
- iswsym_l function
- _iswcsym_l function
- iscsym_l function
- _iscsymf_l function
- _iswcsymf_l function
- _iscsym_l function
- __iscsym function
- __iswcsymf function
- iswsymf_l function
- __iscsymf function
- __iswcsym function
- iscsym function
- iscsymf function
ms.assetid: 944dfb99-f2b8-498c-9f55-dbcf370d0a2c
caps.latest.revision: "21"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3567e6843fc3350d92c6575d320885298140ed50
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="iscsym-iscsymf-iscsym-iswcsym-iscsymf-iswcsymf-iscsyml-iswcsyml-iscsymfl-iswcsymfl"></a>iscsym — iscsymf —, __iscsym —, __iswcsym —, __iscsymf —, __iswcsymf —, _iscsym_l —, _iswcsym_l —, _iscsymf_l —, _iswcsymf_l —

Określanie, czy całkowitą reprezentuje znak, który może być używany w identyfikatorze.

## <a name="syntax"></a>Składnia

```C
int __iscsym(
   int c
);
int __iswcsym(
   wint_t c
);
int __iscsymf(
   int c
);
int __iswcsymf(
   wint_t c
);
int _iscsym_l(
   int c,
   _locale_t locale
);
int _iswcsym_l(
   wint_t c,
   _locale_t locale
);
int _iscsymf_l(
   int c,
   _locale_t locale
);
int _iswcsymf_l(
   wint_t c,
   _locale_t locale
);
#define iscsym __iscsym
#define iscsymf __iscsymf
```

### <a name="parameters"></a>Parametry

*c*  
Liczba całkowita do testowania. *c* powinien być z zakresu od 0 do 255 dla wersji znaki wąskie funkcji.

*Ustawienia regionalne*  
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

Zarówno `__iscsym` i `__iswcsym` zwrócić wartość niezerową, jeśli *c* litera, podkreślenie lub cyfr. Zarówno `__iscsymf` i `__iswcsymf` zwrócić wartość niezerową, jeśli *c* jest literą lub znakiem podkreślenia. Każdy z tych procedur zwraca 0, jeśli *c* nie spełnia warunku. Wersje tych funkcji z `_l` sufiks są identyczne z tą różnicą, że używają one *ustawień regionalnych* przekazana zamiast bieżące ustawienia regionalne dla ich działania zależnego od ustawień regionalnych. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).

## <a name="remarks"></a>Uwagi

Te procedury są definiowane jako makra, chyba że jest zdefiniowane _CTYPE_DISABLE_MACROS makro preprocesora. Gdy używasz wersji makro tych procedur, argumenty może przyjąć więcej niż raz. Należy zachować ostrożność, korzystając z wyrażeń, które ma efekty uboczne w liście argumentów.

W celu zapewnienia zgodności z poprzednimi wersjami `iscsym` i `iscsymf` są zdefiniowane jako makra tylko wtedy, gdy [&#95; &#95; STDC &#95; &#95; ](../../preprocessor/predefined-macros.md) nie został zdefiniowany lub jest zdefiniowany jako 0; w przeciwnym razie zostały zdefiniowane.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|`iscsym`, `iscsymf`, `__iscsym`, `__iswcsym`, `__iscsymf`, `__iswcsymf`, `_iscsym_l`, `_iswcsym_l`, `_iscsymf_l`, `_iswcsymf_l`|C: \<ctype.h ><br /><br /> C++: \<cctype — > lub \<ctype.h >|

`iscsym`, `iscsymf`, `__iscsym`, `__iswcsym`, `__iscsymf`, `__iswcsymf`, `_iscsym_l`, `_iswcsym_l`, `_iscsymf_l`, I `_iswcsymf_l` procedury są określone firmy Microsoft. Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz też

[Klasyfikacja znaków](../../c-runtime-library/character-classification.md)   
[Ustawienia regionalne](../../c-runtime-library/locale.md)   
[is, isw, procedury](../../c-runtime-library/is-isw-routines.md)