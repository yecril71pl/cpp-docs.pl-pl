---
title: mbrtoc16, mbrtoc323 | Dokumentacja firmy Microsoft
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
- mbrtoc16
- mbrtoc32
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
- mbrtoc16
- mbrtoc32
- uchar/mbrtoc16
- uchar/mbrtoc32
dev_langs: C++
helpviewer_keywords:
- mbrtoc16 function
- mbrtoc32 function
ms.assetid: 099ade4d-56f7-4e61-8b45-493f1d7a64bd
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 4f0dcc7490ee6b2d9468bc1c5f83a4585f073295
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="mbrtoc16-mbrtoc32"></a>mbrtoc16, mbrtoc32
Tłumaczy wielobajtowe pierwszego znaku w ciągu typu narrow na równoważne znaku UTF-16 lub UTF-32.  
  
## <a name="syntax"></a>Składnia  
  
```  
size_t mbrtoc16(   
   char16_t* destination,   
   const char* source,   
   size_t max_bytes,   
   mbstate_t* state   
);  
  
size_t mbrtoc32(  
   char32_t* destination,   
   const char* source,   
   size_t max_bytes,   
   mbstate_t* state   
);  
  
```  
  
#### <a name="parameters"></a>Parametry  
 `destination`  
 Wskaźnik do `char16_t` lub `char32_t` równoważne znaków wielobajtowych do konwersji. Jeśli wartość null, funkcja nie przechowuje wartość.  
  
 `source`  
 Wskaźnik do ciągu znaków wielobajtowych do konwersji.  
  
 `max_bytes`  
 Maksymalna liczba bajtów w `source` do sprawdzenia znaku do konwersji. Powinna to być wartość z przedziału od jeden i liczba bajtów, w tym wszelkie terminatorem null w `source`.  
  
 `state`  
 Wskaźnik do `mbstate_t` obiekt stanu konwersji sposób interpretowania wielobajtowe ciąg do co najmniej jeden znak danych wyjściowych.  
  
## <a name="return-value"></a>Wartość zwracana  
 W przypadku powodzenia, zwraca wartość pierwszego z tych warunków, których dotyczy, ponieważ jego bieżący `state` wartość:  
  
|Wartość|Warunek|  
|-----------|---------------|  
|0|Następne `max_bytes` lub mniej znaków skonwertowane z `source` odpowiadają null znaków dwubajtowych jest to wartość, jeśli `destination` nie jest zerowa.<br /><br /> `state`zawiera stan początkowy shift.|  
|Między 1 a `max_bytes`włącznie|Wartość zwracana jest liczba bajtów `source` który ukończyć prawidłowy znaków wielobajtowych. Przekonwertowana znaków dwubajtowych są przechowywane, jeśli `destination` nie jest zerowa.|  
|-3|Następny znak szeroki wynikające z poprzedniego wywołania funkcji przechowywanych w `destination` Jeśli `destination` nie jest zerowa. Brak bajtów z `source` są używane przez wywołanie tej funkcji.<br /><br /> Gdy `source` wskazuje znaków wielobajtowych, która wymaga więcej niż jednego znaku dwubajtowe do reprezentowania (na przykład para zastępcza), a następnie `state` wartość jest aktualizowana, aby następnym wywołaniu funkcji zapisuje się dodatkowych znaków.|  
|-2|Następne `max_bytes` bajty reprezentują ukończona, ale potencjalnie prawidłowy, wielobajtowe znaków. Wartość nie jest przechowywana w `destination`. Wynik ten może wystąpić, jeśli `max_bytes` wynosi zero.|  
|-1|Wystąpił błąd kodowania. Następne `max_bytes` lub mniej bajtów nie wspierają znaków wielobajtowych pełne i prawidłowe. Wartość nie jest przechowywana w `destination`.<br /><br /> `EILSEQ`znajduje się w `errno` i stan konwersji `state` jest nieokreślony.|  
  
## <a name="remarks"></a>Uwagi  
 `mbrtoc16` Funkcja odczytuje do `max_bytes` bajtów z `source` można znaleźć pierwszego znaków wielobajtowych pełną, prawidłowy, a następnie magazynów równoważne UTF-16 znaków w `destination`. Źródło, z jaką bajty są interpretowane zgodnie z bieżącym wielobajtowe ustawienia regionalne wątku. Jeśli znaków wielobajtowych wymaga więcej niż jednego znaku danych wyjściowych UTF-16, takie jak para zastępcza, a następnie `state` ma wartość przechowywania po następnym znaku UTF-16 `destination` na następne wywołanie `mbrtoc16`. `mbrtoc32` Funkcji jest taki sam, ale dane wyjściowe są przechowywane w postaci znaku UTF-32.  
  
 Jeśli `source` ma wartość null, te funkcje, które są zwracane odpowiednikiem połączenie zostało nawiązane przy użyciu argumentów `NULL` dla `destination`, `""` dla `source`, i `1` dla `max_bytes`. Przekazane wartości `destination` i `max_bytes` są ignorowane.  
  
 Jeśli `source` jest niezerowa, funkcja rozpoczyna się od początku ciągu i sprawdza do `max_bytes` bajtów, aby określić liczbę bajtów wymaganą do wykonania następnego znaków wielobajtowych, w tym wszystkie sekwencje shift. Jeśli zbadane bajtów zawiera prawidłowe i kompletne znaków wielobajtowych, funkcja konwertuje znak na równoważne znaków dwubajtowych 16-bitowych lub 32-bitowy lub znaków. Jeśli `destination` jest nie null, funkcja magazynów znak wynik pierwszy (i prawdopodobnie tylko) w lokalizacji docelowej. Jeśli wymagane są dodatkowe dane wyjściowe znaków, wartość jest ustawiana w `state`, dzięki czemu kolejne wywołania funkcji output dodatkowe znaki i zwraca wartość -3. Jeśli żadne więcej danych wyjściowych znaki nie są wymagane, następnie `state` ma ustawioną wartość stanu początkowego przesunięcia.  
  
## <a name="requirements"></a>Wymagania  
  
|Funkcja|Nagłówek C|Nagłówek C++|  
|--------------|--------------|------------------|  
|`mbrtoc16`,                `mbrtoc32`|\<uchar.h >|\<cuchar >|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Konwersja danych](../../c-runtime-library/data-conversion.md)   
 [Ustawienia regionalne](../../c-runtime-library/locale.md)   
 [Interpretacja wielobajtowych sekwencji znaków](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [c16rtomb, c32rtomb](../../c-runtime-library/reference/c16rtomb-c32rtomb1.md)   
 [mbrtowc —](../../c-runtime-library/reference/mbrtowc.md)   
 [mbsrtowcs —](../../c-runtime-library/reference/mbsrtowcs.md)   
 [mbsrtowcs_s —](../../c-runtime-library/reference/mbsrtowcs-s.md)