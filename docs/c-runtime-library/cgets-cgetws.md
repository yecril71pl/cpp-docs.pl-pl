---
title: _cgets —, _cgetws — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
apiname:
- _cgetws
- _cgets
apilocation:
- msvcr100.dll
- msvcr110.dll
- msvcr80.dll
- msvcr120.dll
- msvcr90.dll
- msvcrt.dll
- msvcr110_clr0400.dll
apitype: DLLExport
f1_keywords:
- cgetws
- _cgetws
- _cgets
dev_langs:
- C++
helpviewer_keywords:
- _cgetws function
- strings [C++], getting from console
- console, getting strings from
- _cgets function
- cgetws function
- cgets function
ms.assetid: 4d5e134a-58c3-4f62-befd-5d235b0212f4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 144e08278fb37e08d741ac8cb5a441c8df788b5b
ms.sourcegitcommit: 6e3cf8df676d59119ce88bf5321d063cf479108c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2018
ms.locfileid: "34451201"
---
# <a name="cgets-cgetws"></a>_cgets, _cgetws
Pobiera ciąg znaków z konsoli. Bezpieczniejsza wersje te funkcje są dostępne; zobacz [_cgets_s —, _cgetws_s —](../c-runtime-library/reference/cgets-s-cgetws-s.md).  
  
> [!IMPORTANT]
>  Te funkcje są przestarzałe. Począwszy od programu Visual Studio 2015, ich nie są dostępne w CRT. Bezpieczne wersje tych funkcji, _cgets_s — i _cgetws_s —, są nadal dostępne. Informacje na temat tych funkcji alternatywnych, zobacz [_cgets_s —, _cgetws_s —](../c-runtime-library/reference/cgets-s-cgetws-s.md).  
  
> [!IMPORTANT]
>  Nie można używać tego interfejsu API w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT, nie są obsługiwane w aplikacjach platformy uniwersalnej systemu Windows](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
char *_cgets(   
   char *buffer   
);  
wchar_t *_cgetws(  
   wchar_t *buffer  
);  
template <size_t size>  
char *_cgets(   
   char (&buffer)[size]  
); // C++ only  
template <size_t size>  
wchar_t *_cgetws(  
   wchar_t (&buffer)[size]  
); // C++ only  
```  
  
#### <a name="parameters"></a>Parametry  
 `buffer`  
 Lokalizacja magazynu danych.  
  
## <a name="return-value"></a>Wartość zwracana  
 `_cgets` i `_cgetws` zwraca wskaźnik do początku ciągu znaków na `buffer[2]`. Jeśli `buffer` jest **NULL**, te funkcje Wywołaj program obsługi nieprawidłowych parametrów, zgodnie z opisem w [sprawdzanie poprawności parametru](../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, zwracają **NULL** i ustaw `errno` do `EINVAL`.  
  
## <a name="remarks"></a>Uwagi  
 Tych funkcji odczytu ciąg znaków z konsoli i przechowywane w lokalizacji wskazywanej przez ciąg, a jej długość `buffer`. `buffer` Parametr musi być wskaźnik do tablicy znaków. Pierwszy element tablicy, `buffer[0]`, musi zawierać maksymalną długość (w znakach) ciągu do odczytu. Tablica musi zawierać za mało elementów, aby pomieścić ciąg, znak końcowy null ('\0') i 2 bajty dodatkowe. Funkcja odczytuje znaków, aż do powrotu karetki-wiersza źródła kombinacja (CR LF) lub określoną liczbę znaków jest do odczytu. Ciąg jest przechowywana, zaczynając od `buffer[2]`. Jeśli funkcja CR LF, są przechowywane znak null ('\0'). Funkcja następnie przechowuje rzeczywista długość ciągu drugiego elementu tablicy `buffer[1]`.  
  
 Ponieważ wszystkie klucze edycji są aktywne, kiedy `_cgets` lub `_cgetws` jest wywoływana, gdy w konsoli okna, naciskając klawisz F3 powtarza ostatni wpis wprowadzony.  
  
 W języku C++ te funkcje mają przeciążenia szablonu, które wywołują odpowiedników nowsza, bezpieczne tych funkcji. Aby uzyskać więcej informacji, zobacz [Secure szablonu Overloads](../c-runtime-library/secure-template-overloads.md).  
  
### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu  
  
|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_cgetts`|`_cgets`|`_cgets`|`_cgetws`|  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_cgets`|\<conio.h>|  
|`_cgetws`|\<conio.h > lub \<wchar.h >|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Przykład  
  
```  
// crt_cgets.c  
// compile with: /c /W3  
// This program creates a buffer and initializes  
// the first byte to the size of the buffer. Next, the  
// program accepts an input string using _cgets and displays  
// the size and text of that string.  
  
#include <conio.h>  
#include <stdio.h>  
#include <errno.h>  
  
int main( void )  
{  
   char buffer[83] = { 80 };  // Maximum characters in 1st byte  
   char *result;  
  
   printf( "Input line of text, followed by carriage return:\n");  
  
   // Input a line of text:  
   result = _cgets( buffer ); // C4996  
   // Note: _cgets is deprecated; consider using _cgets_s  
   if (!result)  
   {  
      printf( "An error occurred reading from the console:"  
              " error code %d\n", errno);  
   }  
   else  
   {     
      printf( "\nLine length = %d\nText = %s\n",  
              buffer[1], result );  
   }  
}  
```  
  
```Output  
  
      A line of input.Input line of text, followed by carriage return:  
Line Length = 16  
Text = A line of input.  
```  
  
## <a name="see-also"></a>Zobacz też  
 [We/Wy konsoli i portu](../c-runtime-library/console-and-port-i-o.md)   
 [_getch, _getwch](../c-runtime-library/reference/getch-getwch.md)