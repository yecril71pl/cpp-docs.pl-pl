---
title: "vprintf — funkcje | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apilocation:
- msvcr110.dll
- msvcr120.dll
- msvcr90.dll
- msvcr100.dll
- msvcr110_clr0400.dll
- msvcr80.dll
apitype: DLLExport
f1_keywords: vprintf
dev_langs: C++
helpviewer_keywords:
- vprintf function
- formatted text [C++]
ms.assetid: 02ac7c51-eab1-4bf0-bf4c-77065e3fa744
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 1a888f46912aaa5292e9bcf1f83bc3e6926f73d2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="vprintf-functions"></a>vprintf — Funkcje
Każdy z `vprintf` funkcje przyjmuje wskaźnik do listy argumentów, a następnie formatuje i zapisuje podane dane do określonego miejsca docelowego. Funkcje różnią się sprawdzanie poprawności parametru wykonywane, czy funkcje wykonaj szerokości lub ciągi znaków, miejsce docelowe danych wyjściowych i obsługę określania kolejności, w którym są używane parametry w ciągu formatu.  
  
|||  
|-|-|  
|[_vcprintf —, _vcwprintf —](../c-runtime-library/reference/vcprintf-vcprintf-l-vcwprintf-vcwprintf-l.md)|[vfprintf —, vfwprintf —](../c-runtime-library/reference/vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md)|  
|[_vfprintf_p —, _vfprintf_p_l —, _vfwprintf_p — _vfwprintf_p_l —](../c-runtime-library/reference/vfprintf-p-vfprintf-p-l-vfwprintf-p-vfwprintf-p-l.md)|[vfprintf_s —, _vfprintf_s_l —, vfwprintf_s — _vfwprintf_s_l —](../c-runtime-library/reference/vfprintf-s-vfprintf-s-l-vfwprintf-s-vfwprintf-s-l.md)|  
|[vprintf —, vwprintf —](../c-runtime-library/reference/vprintf-vprintf-l-vwprintf-vwprintf-l.md)|[_vprintf_p —, _vprintf_p_l —, _vwprintf_p — _vwprintf_p_l —](../c-runtime-library/reference/vprintf-p-vprintf-p-l-vwprintf-p-vwprintf-p-l.md)|  
|[vprintf_s —, _vprintf_s_l —, vwprintf_s — _vwprintf_s_l —](../c-runtime-library/reference/vprintf-s-vprintf-s-l-vwprintf-s-vwprintf-s-l.md)|[vsprintf —, vswprintf —](../c-runtime-library/reference/vsprintf-vsprintf-l-vswprintf-vswprintf-l-vswprintf-l.md)|  
|[_vsprintf_p —, _vsprintf_p_l —, _vswprintf_p — _vswprintf_p_l —](../c-runtime-library/reference/vsprintf-p-vsprintf-p-l-vswprintf-p-vswprintf-p-l.md)|[vsprintf_s —, _vsprintf_s_l —, vswprintf_s — _vswprintf_s_l —](../c-runtime-library/reference/vsprintf-s-vsprintf-s-l-vswprintf-s-vswprintf-s-l.md)|  
|[_vscprintf —, _vscprintf_l —, _vscwprintf — _vscwprintf_l —](../c-runtime-library/reference/vscprintf-vscprintf-l-vscwprintf-vscwprintf-l.md)|[_vsnprintf —, _vsnwprintf —](../c-runtime-library/reference/vsnprintf-vsnprintf-vsnprintf-l-vsnwprintf-vsnwprintf-l.md)|  
  
## <a name="remarks"></a>Uwagi  
 `vprintf` Funkcje są podobne do ich odpowiednika funkcje wymienione w poniższej tabeli. Jednak każdy `vprintf` funkcja akceptuje wskaźnik do listy argumentów, podczas gdy każda z funkcji odpowiednikiem akceptuje listy argumentów.  
  
 Te funkcje format danych wyjściowych do miejsc docelowych w następujący sposób.  
  
|Funkcja|Odpowiednik — funkcja|Miejsce docelowe danych wyjściowych|Walidacja parametru|Obsługa parametrów pozycyjnych|  
|--------------|--------------------------|------------------------|--------------------------|----------------------------------|  
|`_vcprintf`|[_cprintf —](../c-runtime-library/reference/cprintf-cprintf-l-cwprintf-cwprintf-l.md)|konsola|Sprawdź, czy wartość null.|Brak|  
|`_vcwprintf`|[_cwprintf —](../c-runtime-library/reference/cprintf-cprintf-l-cwprintf-cwprintf-l.md)|konsola|Sprawdź, czy wartość null.|Brak|  
|`vfprintf`|[fprintf —](../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)|*Strumień*|Sprawdź, czy wartość null.|Brak|  
|**vfprintf_p —**|[fprintf_p —](../c-runtime-library/reference/fprintf-p-fprintf-p-l-fwprintf-p-fwprintf-p-l.md)|*Strumień*|Sprawdź, czy wartości null i prawidłowy format.|Tak|  
|`vfprintf_s`|[fprintf_s —](../c-runtime-library/reference/fprintf-s-fprintf-s-l-fwprintf-s-fwprintf-s-l.md)|*Strumień*|Sprawdź, czy wartości null i prawidłowy format.|Brak|  
|`vfwprintf`|[fwprintf —](../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)|*Strumień*|Sprawdź, czy wartość null.|Brak|  
|**vfwprintf_p —**|[fwprintf_p —](../c-runtime-library/reference/fprintf-p-fprintf-p-l-fwprintf-p-fwprintf-p-l.md)|*Strumień*|Sprawdź, czy wartości null i prawidłowy format.|Tak|  
|`vfwprintf_s`|[fwprintf_s —](../c-runtime-library/reference/fprintf-s-fprintf-s-l-fwprintf-s-fwprintf-s-l.md)|*Strumień*|Sprawdź, czy wartości null i prawidłowy format.|Brak|  
|`vprintf`|[printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)|`Stdout`|Sprawdź, czy wartość null.|Brak|  
|**vprintf_p —**|[printf_p —](../c-runtime-library/reference/printf-p-printf-p-l-wprintf-p-wprintf-p-l.md)|`Stdout`|Sprawdź, czy wartości null i prawidłowy format.|Tak|  
|`vprintf_s`|[printf_s —](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)|`Stdout`|Sprawdź, czy wartości null i prawidłowy format.|Brak|  
|`vwprintf`|[wprintf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)|`Stdout`|Sprawdź, czy wartość null.|Brak|  
|**vwprintf_p —**|[wprintf_p —](../c-runtime-library/reference/printf-p-printf-p-l-wprintf-p-wprintf-p-l.md)|`Stdout`|Sprawdź, czy wartości null i prawidłowy format.|Tak|  
|`vwprintf_s`|[wprintf_s —](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)|`Stdout`|Sprawdź, czy wartości null i prawidłowy format.|Brak|  
|**vsprintf —**|[sprintf —](../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)|pamięć wskazywana przez *buforu*|Sprawdź, czy wartość null.|Brak|  
|**vsprintf_p —**|[sprintf_p —](../c-runtime-library/reference/sprintf-p-sprintf-p-l-swprintf-p-swprintf-p-l.md)|pamięć wskazywana przez *buforu*|Sprawdź, czy wartości null i prawidłowy format.|Tak|  
|`vsprintf_s`|[sprintf_s —](../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md)|pamięć wskazywana przez *buforu*|Sprawdź, czy wartości null i prawidłowy format.|Brak|  
|`vswprintf`|[swprintf —](../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)|pamięć wskazywana przez *buforu*|Sprawdź, czy wartość null.|Brak|  
|**vswprintf_p —**|[swprintf_p —](../c-runtime-library/reference/sprintf-p-sprintf-p-l-swprintf-p-swprintf-p-l.md)|pamięć wskazywana przez *buforu*|Sprawdź, czy wartości null i prawidłowy format.|Tak|  
|`vswprintf_s`|[swprintf_s —](../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md)|pamięć wskazywana przez *buforu*|Sprawdź, czy wartości null i prawidłowy format.|Brak|  
|`_vscprintf`|[_vscprintf —](../c-runtime-library/reference/vscprintf-vscprintf-l-vscwprintf-vscwprintf-l.md)|pamięć wskazywana przez *buforu*|Sprawdź, czy wartość null.|Brak|  
|`_vscwprintf`|[_vscwprintf —](../c-runtime-library/reference/vscprintf-vscprintf-l-vscwprintf-vscwprintf-l.md)|pamięć wskazywana przez *buforu*|Sprawdź, czy wartość null.|Brak|  
|`_vsnprintf`|[_snprintf —](../c-runtime-library/reference/snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md)|pamięć wskazywana przez *buforu*|Sprawdź, czy wartość null.|Brak|  
|`_vsnwprintf`|[_snwprintf —](../c-runtime-library/reference/snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md)|pamięć wskazywana przez *buforu*|Sprawdź, czy wartość null.|Brak|  
  
 `argptr` Argument ma typ `va_list`, która jest zdefiniowana w VARARGS. H i STDARG. H. `argptr` Zmienna musi zostać zainicjowany przez **makra va_start,** i może zostać zainicjowane ponownie przy kolejnych `va_arg` wywołuje; `argptr` następnie wskazuje na początku listy argumentów, które są konwertowane i przesyłane dla danych wyjściowych zgodnie ze specyfikacją odpowiednie w *format* argumentu. *Format* ma taką samą tworzą i działać jako *format* argument [printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md). Żadna z tych funkcji wywołuje `va_end`. Aby uzyskać bardziej szczegółowy opis każdego `vprintf` funkcji, zobacz opis funkcji jego odpowiednik wymienione w powyższej tabeli.  
  
 `_vsnprintf`różni się od **vsprintf —** w tym zapisuje nie więcej niż *liczba* bajtów do *buforu*.  
  
 Wersje tych funkcji z **w** infiksu w nazwie są wersje znaków dwubajtowych odpowiednie funkcje bez **w** element infiksu; w każdej z tych funkcji znaków dwubajtowych  *Bufor* i *format* są ciągami znaków dwubajtowych. W przeciwnym razie każdej funkcji znaków dwubajtowych zachowuje się tak samo dla jej funkcji odpowiednikiem SBCS.  
  
 Wersje tych funkcji z **_s** i **_p** sufiksy są bardziej bezpieczne wersji. Te wersje sprawdzanie poprawności ciągów formatu i wygeneruje wyjątek, jeśli ciąg formatu nie jest poprawnie sformułowany (na przykład, jeśli używane są nieprawidłowe formatowanie znaków).  
  
 Wersje tych funkcji z **_p** sufiks umożliwiają określenie kolejności, w którym mają być zastępowane podanych argumentów w ciągu formatu. Aby uzyskać więcej informacji, zobacz [printf_p parametry pozycyjne](../c-runtime-library/printf-p-positional-parameters.md).  
  
 Aby uzyskać **vsprintf —**, `vswprintf`, `_vsnprintf` i `_vsnwprintf`, jeśli kopiowanie odbywa się między ciągi czy nakładają się na siebie, zachowanie jest niezdefiniowany.  
  
> [!IMPORTANT]
>  Upewnij się, że *format* nie jest ciągiem zdefiniowane przez użytkownika. Aby uzyskać więcej informacji, zobacz [unikanie Overruns buforu](http://msdn.microsoft.com/library/windows/desktop/ms717795). Jeśli przy użyciu bezpiecznych wersji tych funkcji (albo **_s** lub **_p** sufiksy), ciąg formatu dostarczone przez użytkownika może wywołać wyjątek nieprawidłowego parametru, jeśli zawiera ciąg dostarczone przez użytkownika nieprawidłowe znaki formatowania.  
  
## <a name="see-also"></a>Zobacz też  
 [We/Wy strumienia](../c-runtime-library/stream-i-o.md)   
 [fprintf —, _fprintf_l —, fwprintf — _fwprintf_l —](../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)   
 [printf, _printf_l —, wprintf, _wprintf_l —](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)   
 [sprintf, _sprintf_l —, swprintf —, _swprintf_l —, \__swprintf_l —](../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)   
 [va_arg, va_copy, va_end, makra va_start](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)