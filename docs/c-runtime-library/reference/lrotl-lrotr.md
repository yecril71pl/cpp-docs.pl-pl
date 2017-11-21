---
title: "_lrotl —, _lrotr — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _lrotl
- _lrotr
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
- lrotr
- lrotl
- _lrotr
- _lrotl
dev_langs: C++
helpviewer_keywords:
- lrotl function
- bits
- _lrotr function
- lrotr function
- rotating bits
- _lrotl function
- bits, rotating
ms.assetid: d42f295b-35f9-49d2-9ee4-c66896ffe68e
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 25577b776c5a3caf0c47c3cf56a88b7de58392bb
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="lrotl-lrotr"></a>_lrotl, _lrotr
Obracanie bitów w lewo (`_lrotl`) lub w prawo (`_lrotr`).  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      unsigned long _lrotl(  
   unsigned long value,  
   int shift   
);  
unsigned long _lrotr(  
   unsigned long value,  
   int shift   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 *wartość*  
 Wartość, którą można obracać.  
  
 `shift`  
 Liczba bitów, które mają zostać przesunięte *wartość*.  
  
## <a name="return-value"></a>Wartość zwracana  
 Obie funkcje zwracają wartość obrócony. Nie ma żadnych zwracany błąd.  
  
## <a name="remarks"></a>Uwagi  
 `_lrotl` i `_lrotr` Obróć funkcji *wartość* przez `shift` usługi bits. `_lrotl`Obraca wartość w lewo. `_lrotr`Obraca prawej wartości. Funkcjami zawijać bitów obracać wyłączyć jeden z końców *wartość* w innym celu.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_lrotl`|\<stdlib.h >|  
|`_lrotr`|\<stdlib.h >|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="libraries"></a>Biblioteki  
 Wszystkie wersje [biblioteki wykonawcze języka C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="example"></a>Przykład  
  
```  
// crt_lrot.c  
  
#include <stdlib.h>  
#include <stdio.h>  
  
int main( void )  
{  
   unsigned long val = 0x0fac35791;  
  
   printf( "0x%8.8lx rotated left eight times is 0x%8.8lx\n",   
            val, _lrotl( val, 8 ) );  
   printf( "0x%8.8lx rotated right four times is 0x%8.8lx\n",   
            val, _lrotr( val, 4 ) );  
}  
```  
  
## <a name="output"></a>Dane wyjściowe  
  
```  
0xfac35791 rotated left eight times is 0xc35791fa  
0xfac35791 rotated right four times is 0x1fac3579  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)   
 [_rotl —, _rotl64 —, _rotr — _rotr64 —](../../c-runtime-library/reference/rotl-rotl64-rotr-rotr64.md)