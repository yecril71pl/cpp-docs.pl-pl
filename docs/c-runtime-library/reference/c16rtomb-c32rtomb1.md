---
title: c16rtomb, c32rtomb1 | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- c16rtomb
- c32rtomb
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
- api-ms-win-crt-convert-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- c16rtomb
- c32rtomb
- uchar/c16rtomb
- uchar/c32rtomb
dev_langs: C++
helpviewer_keywords:
- c16rtomb function
- c32rtomb function
ms.assetid: 7f5743ca-a90e-4e3f-a310-c73e16f4e14d
caps.latest.revision: "3"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9eb43d6b225bce002eb2ce5293cb048d3062bcd5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="c16rtomb-c32rtomb"></a>c16rtomb, c32rtomb
Przekonwertuj UTF-16 lub UTF-32 znaków dwubajtowych na znaków wielobajtowych w bieżących ustawień regionalnych.  
  
## <a name="syntax"></a>Składnia  
  
```  
size_t c16rtomb(  
    char *mbchar,   
    char16_t wchar,  
    mbstate_t *state  
);  
size_t c32rtomb(  
    char *mbchar,   
    char32_t wchar,  
    mbstate_t *state  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [out]`mbchar`  
 Wskaźnik do tablicy do przechowywania znaków wielobajtowych przekonwertowany.  
  
 [in]`wchar`  
 Szerokie do konwersji.  
  
 [w, out]`state`  
 Wskaźnik do `mbstate_t` obiektu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Liczba bajtów przechowywane w tablicy obiektów `mbchar`, w tym wszystkie sekwencje shift. Jeśli `wchar` nie jest prawidłowym znakiem dwubajtowe, wartość (`size_t`)(-1) jest zwracany, `errno` ustawiono `EILSEQ`i wartość `state` jest nieokreślony.  
  
## <a name="remarks"></a>Uwagi  
 `c16rtomb` Funkcja konwertuje znaków UTF-16 `wchar` równoważne znaków wąskie wielobajtowych sekwencji w bieżących ustawień regionalnych. Jeśli `mbchar` nie jest wskaźnika o wartości null, magazyny funkcja przekonwertowany sekwencji w obiekcie tablicy wskazywana przez `mbchar`. Do `MB_CUR_MAX` bajtów są przechowywane w `mbchar`, i `state` ustawiono Wynikowy stan wielobajtowe shift.    Jeśli `wchar` jest null znaków dwubajtowych wymagane do sekwencji przywracania stanu początkowego przesunięcia są przechowywane w razie potrzeby, następuje znak null i `state` jest ustawiany stan konwersji początkowej. `c32rtomb` Funkcji jest taki sam, ale konwertuje znaków UTF-32.  
  
 Jeśli `mbchar` wskaźnika o wartości null, jest to zachowanie jest odpowiednikiem wywołania funkcji, która zastępuje dla buforu wewnętrznego `mbchar` i międzynarodowe znak null dla `wchar`.  
  
 `state` Obiekt stanu konwersji pozwala na zapewnienie kolejne wywołania tej funkcji i innych ponownego uruchamiania funkcji, które zarządzania stanem shift znaków wielobajtowych danych wyjściowych. Wyniki są niezdefiniowane łączyć użycie funkcji ponownego uruchamiania i bez ponownego uruchamiania lub jeśli wywołanie `setlocale` jest nawiązywane pomiędzy wywołania funkcji ponownego uruchamiania.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`c16rtomb`, `c32rtomb`|C, C++: \<uchar.h >|  
  
 Aby uzyskać informacje dotyczące zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Konwersja danych](../../c-runtime-library/data-conversion.md)   
 [Ustawienia regionalne](../../c-runtime-library/locale.md)   
 [Interpretacja wielobajtowych sekwencji znaków](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [mbrtoc16, mbrtoc32](../../c-runtime-library/reference/mbrtoc16-mbrtoc323.md)   
 [wcrtomb —](../../c-runtime-library/reference/wcrtomb.md)   
 [wcrtomb_s](../../c-runtime-library/reference/wcrtomb-s.md)