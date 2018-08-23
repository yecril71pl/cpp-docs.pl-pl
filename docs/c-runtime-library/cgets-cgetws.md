---
title: _cgets, _cgetws — | Dokumentacja firmy Microsoft
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
- ucrtbase.dll
- api-ms-win-crt-conio-l1-1-0.dll
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
ms.openlocfilehash: 91ae4f6bcd3b32f2d97362d340fad3ef6995802c
ms.sourcegitcommit: e9ce38decc9f986edab5543de3464b11ebccb123
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/13/2018
ms.locfileid: "42466231"
---
# <a name="cgets-cgetws"></a>_cgets, _cgetws
Pobiera ciąg znaków z konsoli. Bardziej bezpieczne wersje tych funkcji są dostępne; zobacz [_cgets_s, _cgetws_s —](../c-runtime-library/reference/cgets-s-cgetws-s.md).  
  
> [!IMPORTANT]
>  Te funkcje są przestarzałe. Począwszy od programu Visual Studio 2015, nie są one dostępne w CRT. Bezpieczne wersje tych funkcji, _cgets_s i _cgetws_s —, są nadal dostępne. Informacje na temat tych funkcji alternatywnych, zobacz [_cgets_s, _cgetws_s —](../c-runtime-library/reference/cgets-s-cgetws-s.md).  
  
> [!IMPORTANT]
>  Tego API nie można używać w aplikacjach korzystających ze środowiska wykonawczego Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platformy uniwersalnej Windows](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).  
  
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
 Lokalizacja magazynowa danych.  
  
## <a name="return-value"></a>Wartość zwracana  
 `_cgets` i `_cgetws` zwracają wskaźnik do początku ciągu, w `buffer[2]`. Jeśli `buffer` jest **NULL**, funkcje te wywołują procedurę obsługi nieprawidłowego parametru, zgodnie z opisem w [Parameter Validation](../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, zwracają one **NULL** i ustaw `errno` do `EINVAL`.  
  
## <a name="remarks"></a>Uwagi  
 Te funkcje odczytują ciąg znaków z konsoli i przechowują ciąg i jego długość w lokalizacji wskazywanej przez `buffer`. `buffer` Parametru musi być wskaźnikiem do tablicy znaków. Pierwszy element tablicy, `buffer[0]`, musi zawierać maksymalną długość (w znakach) ciągu do odczytu. Tablica musi zawierać tyle elementów, aby pomieścić ciąg, kończący znak null (\0) i 2 bajty dodatkowe. Funkcja odczytuje znaki do momentu powrotu karetki — wiersza kanału informacyjnego kombinacji (CR-LF) lub określoną liczbę znaków jest do odczytu. Ciąg jest przechowywany, zaczynając od `buffer[2]`. Jeśli funkcja odczytuje CR-LF, przechowuje znak null ('\0'). Funkcja następnie przechowuje rzeczywista długość ciągu drugiego elementu tablicy, `buffer[1]`.  
  
 Ponieważ wszystkie klawisze edycji są aktywne, kiedy `_cgets` lub `_cgetws` jest wywoływana, gdy w konsoli okna, naciskanie klawisza F3 powtarza ostatni wprowadzony wpis.  
  
 W języku C++ funkcje te mają przeciążenia szablonu, które wywołują nowsze, bezpieczne odpowiedniki tych funkcji. Aby uzyskać więcej informacji, zobacz [Secure przeciążenia szablonu](../c-runtime-library/secure-template-overloads.md).  
  
### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu  
  
|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_cgetts`|`_cgets`|`_cgets`|`_cgetws`|  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_cgets`|\<conio.h>|  
|`_cgetws`|\<conio.h > lub \<wchar.h >|  
  
 Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../c-runtime-library/compatibility.md).  
  
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