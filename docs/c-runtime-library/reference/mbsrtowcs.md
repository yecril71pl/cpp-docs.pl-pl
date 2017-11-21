---
title: "mbsrtowcs — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: mbsrtowcs
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
f1_keywords: mbsrtowcs
dev_langs: C++
helpviewer_keywords: mbsrtowcs function
ms.assetid: f3a29de8-e36e-425b-a7fa-a258e6d7909d
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: e2e3a202eb50159c43c57c96f785c74156336af8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="mbsrtowcs"></a>mbsrtowcs
Konwertuje ciąg znaków wielobajtowych w bieżących ustawień regionalnych na odpowiedni ciąg znaków typu wide, z możliwością ponownego uruchomienia w środku znaków wielobajtowych. Bezpieczniejsza wersja ta funkcja jest dostępna; zobacz [mbsrtowcs_s —](../../c-runtime-library/reference/mbsrtowcs-s.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
size_t mbsrtowcs(  
   wchar_t *wcstr,  
   const char **mbstr,  
   sizeof count,  
   mbstate_t *mbstate  
);  
template <size_t size>  
size_t mbsrtowcs(  
   wchar_t (&wcstr)[size],  
   const char **mbstr,  
   sizeof count,  
   mbstate_t *mbstate  
); // C++ only  
```  
  
#### <a name="parameters"></a>Parametry  
 [out]`wcstr`  
 Adres do przechowywania powstałe w ten sposób konwersji ciągu znaków dwubajtowych.  
  
 [w, out]`mbstr`  
 Pośredni wskaźnik do lokalizacji ciąg znaków wielobajtowych do przekonwertowania.  
  
 [in]`count`  
 Maksymalną liczbę znaków (nie w bajtach), aby przekonwertować i przechowywać w `wcstr`.  
  
 [w, out]`mbstate`  
 Wskaźnik do `mbstate_t` konwersji stanu obiektu. Jeśli ta wartość jest wskaźnika o wartości null, jest używany obiekt stanu statyczne wewnętrzne konwersji. Ponieważ wewnętrznej `mbstate_t` obiekt nie jest bezpieczne wątkowo, zaleca się, że należy zawsze przekazuj własne `mbstate` parametru.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca liczbę znaków pomyślnie przekonwertowany, nie włączając znak końcowy null. Zwraca (size_t)(-1), jeśli wystąpił błąd i ustawia `errno` do eilseq —.  
  
## <a name="remarks"></a>Uwagi  
 `mbsrtowcs` Funkcja konwertuje ciąg znaków wielobajtowych pośrednio wskazywana przez `mbstr`, w znaki dwubajtowe są przechowywane w buforze wskazywana przez `wcstr`, za pomocą konwersji stanie zawartymi w `mbstate`. Konwersja będzie wykonywany dla każdego znaku do momentu napotkano albo Trwa przerywanie działania null znaków wielobajtowych napotkano wielobajtowych sekwencji, która nie odpowiada nieprawidłowy znak w bieżących ustawień regionalnych, lub do czasu `count` zostały znaków przekonwertowany. Jeśli `mbsrtowcs` napotka znaków wielobajtowych null ('\0'), przed lub po `count` występuje i konwertuje ją na znak końcowy null 16-bitowych i kończy działanie.  
  
 W związku z tym ciągu znaków typu wide `wcstr` jest zakończony wartością null tylko wtedy, gdy `mbsrtowcs` napotka znaków wielobajtowych wartości null podczas konwersji. Jeśli sekwencje wskazywana przez `mbstr` i `wcstr` nakładają się zachowanie `mbsrtowcs` jest niezdefiniowana. `mbsrtowcs`ma to wpływ na poszczególnych kategorii LC_TYPE bieżące ustawienia regionalne.  
  
 `mbsrtowcs` Funkcja różni się od [mbstowcs —, _mbstowcs_l —](../../c-runtime-library/reference/mbstowcs-mbstowcs-l.md) przez jego restartability. Stan konwersji jest przechowywany w `mbstate` dla kolejnych wywołań w tej samej lub innych funkcji ponownego uruchamiania. Wyniki są niezdefiniowane, gdy mieszanie korzystanie z funkcji ponownego uruchamiania i nonrestartable.  Na przykład, aplikacja, należy użyć `mbsrlen` zamiast `mbslen`, jeśli kolejne wywołanie `mbsrtowcs` jest używany zamiast`mbstowcs.`  
  
 Jeśli `wcstr` wskaźnika o wartości null, nie jest obiekt wskaźnika wskazywana przez `mbstr` jest przypisany wskaźnika o wartości null, jeśli konwersja została zatrzymana, ponieważ osiągnięto znak końcowy null. W przeciwnym razie wartość przypisano adres przeszłości tylko ostatnich znaków wielobajtowych przekonwertowany, jeśli istnieje. Umożliwia wywołanie funkcji kolejne ponowne uruchomienie konwersji, gdzie to wywołanie jest zatrzymana.  
  
 Jeśli `wcstr` argument jest pusty wskaźnik `count` argument jest ignorowany i `mbsrtowcs` zwraca wymagany rozmiar w znaki dwubajtowe ciągu docelowego. Jeśli `mbstate` jest wskaźnika o wartości null, funkcja używa statycznego z systemem innym niż wątkowo wewnętrzny `mbstate_t` konwersji stanu obiektu. Jeśli sekwencja znaków `mbstr` nie ma odpowiedniego wielobajtowe reprezentacji znaków, zwracany jest -1 i `errno` ma ustawioną wartość `EILSEQ`.  
  
 Jeśli `mbstr` isa wskaźnika o wartości null, program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może kontynuować, ta funkcja ustawia `errno` do `EINVAL` i zwraca wartość -1.  
  
 W języku C++ ta funkcja ma przeciążenia szablonów, które wywołuje nowsza, bezpieczne odpowiednikiem tej funkcji. Aby uzyskać więcej informacji, zobacz [Secure szablonu Overloads](../../c-runtime-library/secure-template-overloads.md).  
  
## <a name="exceptions"></a>Wyjątki  
 `mbsrtowcs` Funkcji jest bezpieczne wielowątkowe tak długo, jak wywołuje żadnej funkcji w bieżącym wątku `setlocale` tak długo, jak ta funkcja jest wykonywany i `mbstate` argument nie jest wskaźnika o wartości null.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`mbsrtowcs`|\<WChar.h >|  
  
## <a name="see-also"></a>Zobacz też  
 [Konwersja danych](../../c-runtime-library/data-conversion.md)   
 [Ustawienia regionalne](../../c-runtime-library/locale.md)   
 [Interpretacja wielobajtowych sekwencji znaków](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [mbrtowc —](../../c-runtime-library/reference/mbrtowc.md)   
 [mbtowc —, _mbtowc_l —](../../c-runtime-library/reference/mbtowc-mbtowc-l.md)   
 [mbstowcs —, _mbstowcs_l —](../../c-runtime-library/reference/mbstowcs-mbstowcs-l.md)   
 [mbsinit —](../../c-runtime-library/reference/mbsinit.md)