---
title: "_lsearch_s — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _lsearch_s
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
- api-ms-win-crt-utility-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _lsearch_s
- lsearch_s
dev_langs: C++
helpviewer_keywords:
- linear searching
- values, searching for
- keys, finding in arrays
- arrays [CRT], searching
- searching, linear
- _lsearch_s function
- lsearch_s function
ms.assetid: d2db0635-be7a-4799-8660-255f14450882
caps.latest.revision: "17"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: cb44e7b2c79b1e8719768634bfe028207b9e8d11
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="lsearchs"></a>_lsearch_s
Wykonuje wyszukiwanie liniowe dla wartości. Wersja [_lsearch —](../../c-runtime-library/reference/lsearch.md) ulepszeń zabezpieczeń zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
void *_lsearch_s(  
   const void *key,  
   void *base,  
   unsigned int *num,  
   size_t size,  
   int (__cdecl *compare)(void *, const void *, const void *),  
   void * context  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `key`  
 Obiekt do wyszukania.  
  
 `base`  
 Wskaźnik do podstawy tablicy do wyszukania.  
  
 `num`  
 Liczba elementów.  
  
 `size`  
 Rozmiar każdy element tablicy bajtów.  
  
 `compare`  
 Wskaźnik do procedury porównania. Drugi parametr jest wskaźnik do klucza dla wyszukiwania. Trzeci parametr jest wskaźnik do elementu tablicy ma zostać porównane z kluczem.  
  
 `context`  
 Wskaźnik do obiektu, który mogą być używane w funkcji porównania.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli `key` zostanie znaleziony, `_lsearch_s` zwraca wskaźnik do elementu tablicy w `base` , które odpowiadają `key`. Jeśli `key` nie zostanie znaleziony, `_lsearch_s` zwraca wskaźnik do nowo dodany element na końcu tablicy.  
  
 Jeśli nieprawidłowe parametry są przekazywane do funkcji, program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, następnie `errno` ustawiono `EINVAL` i funkcja zwraca `NULL`. Aby uzyskać więcej informacji, zobacz [errno _doserrno —, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
### <a name="error-conditions"></a>Warunki błędów  
  
|`key`|`base`|`compare`|`num`|`size`|`errno`|  
|-----------|------------|---------------|-----------|------------|-------------|  
|`NULL`|wszystkie|wszystkie|wszystkie|wszystkie|`EINVAL`|  
|wszystkie|`NULL`|wszystkie|!= 0|wszystkie|`EINVAL`|  
|wszystkie|wszystkie|wszystkie|wszystkie|zero|`EINVAL`|  
|wszystkie|wszystkie|`NULL`|Wystąpił|wszystkie|`EINVAL`|  
  
## <a name="remarks"></a>Uwagi  
 `_lsearch_s` Funkcja wykonuje wyszukiwanie liniowe dla wartości `key` w tablicy `num` z elementów `width` bajtów. W odróżnieniu od `bsearch_s`, `_lsearch_s` nie wymaga tablicy ma zostać posortowana. Jeśli `key` nie zostanie znaleziony, następnie `_lsearch_s` dodaje go do końca tablicy i zwiększa `num`.  
  
 `compare` Funkcji jest wskaźnikiem do procedury dostarczone przez użytkownika, który porównuje dwa elementy tablicy i zwraca wartość określającą ich relacji. `compare` Funkcja przyjmuje również wskaźnik do kontekstu jako pierwszego argumentu. `_lsearch_s`wywołania `compare` jeden lub więcej razy podczas wyszukiwania przekazywanie wskaźników do dwóch elementów tablicy przy każdym wywołaniu. `compare`należy porównać elementy, a następnie wróć albo różną od zera (to znaczy elementy są inne) lub wartość 0 (tzn. elementy są identyczne).  
  
 `context` Wskaźnika może być przydatna, jeśli struktura przeszukane danych jest częścią obiektu i `compare` funkcji ma dostęp do elementów członkowskich obiektu. Na przykład kodu w `compare` funkcji można rzutować wskaźnika void do odpowiedniego obiektu członków typu i dostępu do tego obiektu. Dodanie `context` sprawia, że wskaźnik `_lsearch_s` bardziej bezpieczne, ponieważ dodatkowy kontekst mogą zostać użyte w celu uniknięcia ponownego rozpoczęcia błędów związanych z użyciem zmienne statyczne, aby udostępnić dane `compare` funkcji.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_lsearch_s`|\<Search.h >|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="see-also"></a>Zobacz też  
 [Wyszukiwanie i sortowanie](../../c-runtime-library/searching-and-sorting.md)   
 [bsearch_s —](../../c-runtime-library/reference/bsearch-s.md)   
 [_lfind_s —](../../c-runtime-library/reference/lfind-s.md)   
 [_lsearch —](../../c-runtime-library/reference/lsearch.md)