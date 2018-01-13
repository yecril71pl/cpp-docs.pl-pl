---
title: "mbsrtowcs_s — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: mbsrtowcs_s
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
f1_keywords: mbsrtowcs_s
dev_langs: C++
helpviewer_keywords: mbsrtowcs_s function
ms.assetid: 4ee084ec-b15d-4e5a-921d-6584ec3b5a60
caps.latest.revision: "24"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b701362fd8ed19575f5de34f998bc8fd4f7e6de1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="mbsrtowcss"></a>mbsrtowcs_s
Konwertowanie ciągu znaków wielobajtowych w bieżących ustawień regionalnych reprezentacji ciągu znaków dwubajtowych. Wersja [mbsrtowcs —](../../c-runtime-library/reference/mbsrtowcs.md) ulepszeń zabezpieczeń zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
errno_t mbsrtowcs_s(  
   size_t * pReturnValue,  
   wchar_t * wcstr,  
   size_t sizeInWords,  
   const char ** mbstr,  
   size_t count,  
   mbstate_t * mbstate  
);  
template <size_t size>  
errno_t mbsrtowcs_s(  
   size_t * pReturnValue,  
   wchar_t (&wcstr)[size],  
   const char ** mbstr,  
   size_t count,  
   mbstate_t * mbstate  
); // C++ only  
```  
  
#### <a name="parameters"></a>Parametry  
 [out]`pReturnValue`  
 Liczba znaków konwersji.  
  
 [out]`wcstr`  
 Adres buforu do przechowywania powstałe w ten sposób konwersji ciągu znaków dwubajtowych.  
  
 [out]`sizeInWords`  
 Rozmiar `wcstr` słownie (znaki dwubajtowe).  
  
 [w, out]`mbstr`  
 Pośredni wskaźnik do lokalizacji ciąg znaków wielobajtowych do skonwertowania.  
  
 [in]`count`  
 Maksymalna liczba znaki dwubajtowe, które mają być przechowywane w `wcstr` buforu Trwa przerywanie działania wartość null, z wyłączeniem lub [_truncate —](../../c-runtime-library/truncate.md).  
  
 [w, out]`mbstate`  
 Wskaźnik do `mbstate_t` konwersji stanu obiektu. Jeśli ta wartość jest wskaźnika o wartości null, jest używany obiekt stanu statyczne wewnętrzne konwersji. Ponieważ wewnętrznej `mbstate_t` obiekt nie jest bezpieczne wątkowo, zaleca się, że należy zawsze przekazuj własne `mbstate` parametru.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zero, jeśli konwersja zakończy się pomyślnie, lub błąd o kodzie błędu.  
  
|Warunek błędu|Wartość zwracana i`errno`|  
|---------------------|------------------------------|  
|`wcstr`wskaźnik null i `sizeInWords` > 0.|`EINVAL`|  
|`mbstr`wskaźnik null|`EINVAL`|  
|Ciąg pośrednio wskazywana przez `mbstr` zawiera sekwencję wielobajtowe, która jest nieprawidłowa dla bieżącego ustawienia regionalne.|`EILSEQ`|  
|Bufor docelowy jest zbyt mały, aby pomieścił skonwertowany ciąg (chyba że `count` jest `_TRUNCATE`; Aby uzyskać więcej informacji, zobacz Uwagi)|`ERANGE`|  
  
 Jeśli występuje jeden z tych warunków, nieprawidłowy parametr wyjątek jest wywoływany zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md) . Jeśli wykonanie może kontynuować, funkcja zwraca błąd o kodzie i ustawia `errno` wymienione w tabeli.  
  
## <a name="remarks"></a>Uwagi  
 `mbsrtowcs_s` Funkcja konwertuje ciąg znaków wielobajtowych pośrednio wskazywana przez `mbstr` w znaki dwubajtowe są przechowywane w buforze wskazywana przez `wcstr`, za pomocą konwersji stanie zawartymi w `mbstate`. Konwersja będzie kontynuowane dla każdego znaku, dopóki spełniony jest jeden z następujących warunków:  
  
-   Napotkano znak null wielobajtowe  
  
-   Napotkano nieprawidłowy znaków wielobajtowych  
  
-   Liczba znaki dwubajtowe są przechowywane w `wcstr` buforu equals `count`.  
  
 Ciąg docelowego `wcstr` jest zawsze zerem, nawet w przypadku błędu, chyba że `wcstr` jest wskaźnika o wartości null.  
  
 Jeśli `count` jest specjalna wartość [_truncate —](../../c-runtime-library/truncate.md), `mbsrtowcs_s` konwertuje tyle ciągu jako spowoduje mieści się w bufor docelowy pozostawiając nadal miejsca dla terminatora o wartości null.  
  
 Jeśli `mbsrtowcs_s` pomyślnie konwertuje ciąg źródłowy umieszcza w znaki dwubajtowe skonwertowany ciąg i terminatorem null do rozmiaru `*pReturnValue`, podany `pReturnValue` nie jest wskaźnika o wartości null. Dzieje się tak nawet wtedy, gdy `wcstr` argument jest pusty wskaźnik i umożliwia określenie wymagany rozmiar buforu. Należy pamiętać, że jeśli `wcstr` wskaźnika o wartości null, jest `count` jest ignorowana.  
  
 Jeśli `wcstr` wskaźnika o wartości null, nie jest obiekt wskaźnika wskazywana przez `mbstr` jest przypisany wskaźnika o wartości null, jeśli konwersja została zatrzymana, ponieważ osiągnięto znak końcowy null. W przeciwnym razie wartość przypisano adres przeszłości tylko ostatnich znaków wielobajtowych przekonwertowany, jeśli istnieje. Umożliwia wywołanie funkcji kolejne ponowne uruchomienie konwersji, gdzie to wywołanie jest zatrzymana.  
  
 Jeśli `mbstate` jest pustego wskaźnika wewnętrznego biblioteki `mbstate_t` obiektu statycznego stan konwersji jest używany. Ten wewnętrzny obiekt statycznych nie jest bezpieczne wątkowo, dlatego zaleca się że przekazujesz własne `mbstate` wartość.  
  
 Jeśli `mbsrtowcs_s` napotka znaków wielobajtowych, który nie jest prawidłowa w bieżących ustawień regionalnych, umieszcza -1 w `*pReturnValue`, ustawia bufor docelowy `wcstr` na pusty ciąg, ustawia `errno` do `EILSEQ`i zwraca `EILSEQ`.  
  
 Jeśli sekwencje wskazywana przez `mbstr` i `wcstr` nakładają się zachowanie `mbsrtowcs_s` jest niezdefiniowana. `mbsrtowcs_s`ma to wpływ na poszczególnych kategorii LC_TYPE bieżące ustawienia regionalne.  
  
> [!IMPORTANT]
>  Upewnij się, że `wcstr` i `mbstr` nie pokrywają oraz że `count` poprawnie odzwierciedla liczbę znaków wielobajtowych do konwersji.  
  
 `mbsrtowcs_s` Funkcja różni się od [mbstowcs_s —, _mbstowcs_s_l —](../../c-runtime-library/reference/mbstowcs-s-mbstowcs-s-l.md) przez jego restartability. Stan konwersji jest przechowywany w `mbstate` dla kolejnych wywołań w tej samej lub innych funkcji ponownego uruchamiania. Wyniki są niezdefiniowane, gdy mieszanie korzystanie z funkcji ponownego uruchamiania i nonrestartable. Na przykład, aplikacja, należy użyć `mbsrlen` zamiast `mbslen`, jeśli kolejne wywołanie `mbsrtowcs_s` jest używany zamiast`mbstowcs_s.`  
  
 W języku C++ za pomocą tej funkcji zostało uproszczone dzięki przeciążenia szablonu; przeciążeń można automatycznie rozpoznać długość buforu (eliminując konieczność określić argument rozmiar) i automatycznie można zastąpić starszą, które nie są bezpieczne funkcje za pomocą ich odpowiedniki nowsza, bezpieczne. Aby uzyskać więcej informacji, zobacz [Secure szablonu Overloads](../../c-runtime-library/secure-template-overloads.md).  
  
## <a name="exceptions"></a>Wyjątki  
 `mbsrtowcs_s` Funkcji jest bezpieczne wielowątkowe, jeśli brak funkcji w bieżącym wywołania wątku `setlocale` tak długo, jak ta funkcja jest wykonywany i `mbstate` argument nie jest wskaźnika o wartości null.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`mbsrtowcs_s`|\<WChar.h >|  
  
## <a name="see-also"></a>Zobacz też  
 [Konwersja danych](../../c-runtime-library/data-conversion.md)   
 [Ustawienia regionalne](../../c-runtime-library/locale.md)   
 [Interpretacja wielobajtowych sekwencji znaków](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [mbrtowc —](../../c-runtime-library/reference/mbrtowc.md)   
 [mbtowc —, _mbtowc_l —](../../c-runtime-library/reference/mbtowc-mbtowc-l.md)   
 [mbstowcs_s —, _mbstowcs_s_l —](../../c-runtime-library/reference/mbstowcs-s-mbstowcs-s-l.md)   
 [mbsinit](../../c-runtime-library/reference/mbsinit.md)