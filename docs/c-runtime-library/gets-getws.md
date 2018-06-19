---
title: pobiera _getws — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
apiname:
- _getws
- gets
apilocation:
- msvcr80.dll
- msvcr90.dll
- msvcr120.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcrt.dll
- msvcr100.dll
apitype: DLLExport
f1_keywords:
- _getts
- gets
- _getws
dev_langs:
- C++
helpviewer_keywords:
- getws function
- getts function
- _getws function
- lines, getting
- streams, getting lines
- _getts function
- gets function
- standard input, reading from
ms.assetid: 1ec2dd4b-f801-48ea-97c2-892590f16024
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a597ad1a72f903d08e848727045e05bf014879b1
ms.sourcegitcommit: 6e3cf8df676d59119ce88bf5321d063cf479108c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2018
ms.locfileid: "34450640"
---
# <a name="gets-getws"></a>gets, _getws
Pobiera wiersza ze `stdin` strumienia. Bezpieczniejsza wersje te funkcje są dostępne; zobacz [gets_s —, _getws_s —](../c-runtime-library/reference/gets-s-getws-s.md).  
  
> [!IMPORTANT]
>  Te funkcje są przestarzałe. Począwszy od programu Visual Studio 2015, ich nie są dostępne w CRT. Bezpieczne wersje tych funkcji, gets_s — i _getws_s —, są nadal dostępne. Informacje na temat tych funkcji alternatywnych, zobacz [gets_s —, _getws_s —](../c-runtime-library/reference/gets-s-getws-s.md).  
  
> [!IMPORTANT]
>  Nie można używać tego interfejsu API w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT, nie są obsługiwane w aplikacjach platformy uniwersalnej systemu Windows](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
char *gets(   
   char *buffer   
);  
wchar_t *_getws(   
   wchar_t *buffer   
);  
template <size_t size>  
char *gets(   
   char (&buffer)[size]  
); // C++ only  
template <size_t size>  
wchar_t *_getws(   
   wchar_t (&buffer)[size]  
); // C++ only  
```  
  
#### <a name="parameters"></a>Parametry  
 `buffer`  
 Lokalizacja magazynu dla ciągu wejściowego.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca jej argument. A **NULL** wskaźnik wskazuje błąd lub końca pliku. Użyj [ferror —](../c-runtime-library/reference/ferror.md) lub [feof —](../c-runtime-library/reference/feof.md) ustalenie, który wystąpił. Jeśli `buffer` jest **NULL**, te funkcje Wywołaj program obsługi nieprawidłowych parametrów, zgodnie z opisem w [sprawdzanie poprawności parametru](../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, te funkcje zwracają **NULL** ustawiono errno `EINVAL`.  
  
## <a name="remarks"></a>Uwagi  
 `gets` Funkcja odczytuje wiersz z Standardowy strumień wejściowy `stdin` i przechowuje ją w `buffer`. Wiersz składa się z wszystkich znaków, w tym pierwszym znakiem nowego wiersza ("\n"). `gets` następnie zastępuje znaku nowego wiersza znak null ('\0') przed powrotem z wiersza. Z kolei `fgets` funkcja zachowuje znaku nowego wiersza. `_getws` jest to wersja znaków dwubajtowych `gets`; jego argumentów i wartości zwracanej są ciągami znaków dwubajtowych.  
  
> [!IMPORTANT]
>  Ponieważ nie istnieje żaden sposób, aby ograniczyć liczbę znaków do odczytu przez pobiera, niezaufanych danych wejściowych łatwo może powodować przepełnienia buforu. Zamiast nich należy używać słów kluczowych `fgets`.  
  
 W języku C++ te funkcje mają przeciążenia szablonu, które wywołują odpowiedników nowsza, bezpieczne tych funkcji. Aby uzyskać więcej informacji, zobacz [Secure szablonu Overloads](../c-runtime-library/secure-template-overloads.md).  
  
### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu  
  
|Procedura TCHAR.H|_Unicode — & _MBCS nie zdefiniowany|_MBCS zdefiniowano|_UNICODE zdefiniowano|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_getts`|`gets`|`gets`|`_getws`|  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`gets`|\<stdio.h>|  
|`_getws`|\<stdio.h > lub \<wchar.h >|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Przykład  
  
```  
// crt_gets.c  
// compile with: /WX /W3  
  
#include <stdio.h>  
  
int main( void )  
{  
   char line[21]; // room for 20 chars + '\0'  
   gets( line );  // C4996  
   // Danger: No way to limit input to 20 chars.  
   // Consider using gets_s instead.  
   printf( "The line entered was: %s\n", line );  
}  
```  
  
 Należy pamiętać, że dane wejściowe dłuższa niż 20 znaków spowoduje przepełnienie buforu wiersza i prawie na pewno spowodować awarię programu.  
  
```Output  
  
Hello there!The line entered was: Hello there!  
```  
  
## <a name="see-also"></a>Zobacz też  
 [We/Wy strumienia](../c-runtime-library/stream-i-o.md)   
 [fgets —, fgetws —](../c-runtime-library/reference/fgets-fgetws.md)   
 [fputs —, fputws —](../c-runtime-library/reference/fputs-fputws.md)   
 [puts, _putws](../c-runtime-library/reference/puts-putws.md)