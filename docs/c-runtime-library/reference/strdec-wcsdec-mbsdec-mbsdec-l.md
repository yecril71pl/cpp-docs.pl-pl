---
title: _strdec, _wcsdec, _mbsdec, _mbsdec_l | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _wcsdec
- _strdec
- _mbsdec
- _mbsdec_l
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
- _strdec
- mbsdec_l
- strdec
- _mbsdec
- _mbsdec_l
- mbsdec
- wcsdec
- _wcsdec
dev_langs: C++
helpviewer_keywords:
- mbsdec_l function
- mbsdec function
- tcsdec function
- _tcsdec function
- _strdec function
- _wcsdec function
- _mbsdec_l function
- strdec function
- wcsdec function
- _mbsdec function
ms.assetid: ae37c223-800f-48a9-ae8e-38c8d20af2dd
caps.latest.revision: "24"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 4df8de18c2256b4e9034b4b0c80f7c4edf85fe91
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="strdec-wcsdec-mbsdec-mbsdecl"></a>_strdec, _wcsdec, _mbsdec, _mbsdec_l
Przenosi ciąg wskaźnik wstecz o jeden znak.  
  
> [!IMPORTANT]
>  `mbsdec`i `mbsdec_l` nie można używać w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT, nie są obsługiwane z parametrem /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Składnia  
  
```  
unsigned char *_strdec(  
   const unsigned char *start,  
   const unsigned char *current   
);  
unsigned wchar_t *_wcsdec(  
   const unsigned wchar_t *start,  
   const unsigned wchar_t *current   
);  
unsigned char *_mbsdec(  
   const unsigned char *start,  
   const unsigned char *current   
);  
unsigned char *_mbsdec_l(  
   const unsigned char *start,  
   const unsigned char *current,  
   _locale_t locale  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `start`  
 Wskaźnik do dowolnego znaku (lub `_mbsdec` i `_mbsdec_l`, pierwszy bajt znaków wielobajtowych) w ciągu źródłowego; `start` musi poprzedzać `current` w ciągu źródła.  
  
 `current`  
 Wskaźnik do dowolnego znaku (lub `_mbsdec` i `_mbsdec_l`, pierwszy bajt znaków wielobajtowych) w ciągu źródłowego; `current` wykonaj `start` w ciągu źródła.  
  
 `locale`  
 Ustawienia regionalne do użycia.  
  
## <a name="return-value"></a>Wartość zwracana  
 `_mbsdec`, `_mbsdec_l`, `_strdec`, i `_wcsdec` znak, który bezpośrednio przed każdym zwraca wskaźnik `current`; `_mbsdec` zwraca `NULL` Jeśli wartość `start` jest większa lub równa tej właściwości `current`. `_tcsdec`mapy do jednej z tych funkcji i zwracanych wartości zależy od mapowania.  
  
## <a name="remarks"></a>Uwagi  
 `_mbsdec` i `_mbsdec_l` funkcje zwraca wskaźnik do pierwszego bajtu znaków wielobajtowych, znajdującego się bezpośrednio przed `current` w ciągu, który zawiera `start`.  
  
 Wartość wyjściowa jest zagrożony ustawienie `LC_CTYPE` ustawienie kategorii ustawień regionalnych; zobacz [setlocale, _wsetlocale —](../../c-runtime-library/reference/setlocale-wsetlocale.md) Aby uzyskać więcej informacji.  `_mbsdec`rozpoznaje wielobajtowych sekwencji znaków zgodnie z ustawień regionalnych, który jest obecnie używany, gdy `_mbsdec_l` jest identyczny z tą różnicą, że parametr ustawień regionalnych, który jest przekazywany w zamian używa. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).  
  
 Jeśli `start` lub `current` jest `NULL`, program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, ta funkcja zwraca `EINVAL` i ustawia `errno` do `EINVAL`.  
  
> [!IMPORTANT]
>  Funkcje te mogą być podatne na zagrożenia przepełnienie buforu. Przepełnienia buforów może służyć do ataków systemu, ponieważ mogą one powodować nieuzasadnione podniesienie uprawnień. Aby uzyskać więcej informacji, zobacz [unikanie Overruns buforu](http://msdn.microsoft.com/library/windows/desktop/ms717795).  
  
### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu  
  
|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_tcsdec`|`_strdec`|`_mbsdec`|`_wcsdec`|  
  
 `_strdec`i `_wcsdec` pojedynczych bajtów znaków i znaków dwubajtowych wersji `_mbsdec` i `_mbsdec_l`. `_strdec`i `_wcsdec` są dostępne tylko dla tego mapowania i nie powinna być używana w inny sposób.  
  
 Aby uzyskać więcej informacji, zobacz [przy użyciu mapowania zwykłego tekstu](../../c-runtime-library/using-generic-text-mappings.md) i [mapowania zwykłego tekstu](../../c-runtime-library/generic-text-mappings.md).  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|Opcjonalne nagłówki|  
|-------------|---------------------|---------------------|  
|`_mbsdec`|\<mbstring.h >|\<mbctype.h >|  
|`_mbsdec_l`|\<mbstring.h >|\<mbctype.h >|  
|`_strdec`|\<tchar.h >||  
|`_wcsdec`|\<tchar.h >||  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono użycie `_tcsdec`.  
  
```  
  
      #include <iostream>  
#include <tchar.h>  
using namespace std;  
  
int main()  
{  
   const TCHAR *str = _T("12345");  
   cout << "str: " << str << endl;  
  
   const TCHAR *str2;  
   str2 = str + 2;  
   cout << "str2: " << str2 << endl;  
  
   TCHAR *answer;  
   answer = _tcsdec( str, str2 );  
   cout << "answer: " << answer << endl;  
  
   return (0);   
}  
  
```  
  
 W poniższym przykładzie przedstawiono użycie `_mbsdec`.  
  
```  
#include <iostream>  
#include <mbstring.h>  
using namespace std;  
  
int main()   
{   
   char *str = "12345";  
   cout << "str: " << str << endl;  
  
   char *str2;  
   str2 = str + 2;   
   cout << "str2: " << str2 << endl;  
  
   unsigned char *answer;  
   answer = _mbsdec( reinterpret_cast<unsigned char *>( str ), reinterpret_cast<unsigned char *>( str2 ));  
  
   cout << "answer: " << answer << endl;  
  
   return (0);   
}  
  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Manipulowanie ciągami](../../c-runtime-library/string-manipulation-crt.md)   
 [_strinc, _wcsinc, _mbsinc, _mbsinc_l](../../c-runtime-library/reference/strinc-wcsinc-mbsinc-mbsinc-l.md)   
 [_strnextc, _wcsnextc, _mbsnextc, _mbsnextc_l](../../c-runtime-library/reference/strnextc-wcsnextc-mbsnextc-mbsnextc-l.md)   
 [_strninc, _wcsninc, _mbsninc, _mbsninc_l](../../c-runtime-library/reference/strninc-wcsninc-mbsninc-mbsninc-l.md)