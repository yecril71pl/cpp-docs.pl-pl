---
title: "_outp —, _outpw —, _outpd — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _outpd
- _outp
- _outpw
apilocation:
- msvcrt.dll
- msvcr100.dll
- msvcr120.dll
- msvcr90.dll
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcr80.dll
apitype: DLLExport
f1_keywords:
- _outpw
- _outpd
- _outp
- outpd
dev_langs:
- C++
helpviewer_keywords:
- outpw function
- words
- _outpd function
- outpd function
- outp function
- ports, writing bytes at
- bytes, writing to ports
- words, writing to ports
- double words
- double words, writing to ports
- _outpw function
- _outp function
ms.assetid: c200fe22-41f6-46fd-b0be-ebb805b35181
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8f2b32b17ed65120aa98b19ed3b2cf599364fee0
ms.sourcegitcommit: a5916b48541f804a79891ff04e246628b5f9a24a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2018
---
# <a name="outp-outpw-outpd"></a>_outp, _outpw, _outpd
Dane wyjściowe w porcie bajt (`_outp`), wyraz (`_outpw`), lub word o podwójnej precyzji (`_outpd`).  
  
> [!IMPORTANT]
>  Te funkcje są przestarzałe. Począwszy od programu Visual Studio 2015, ich nie są dostępne w CRT.  
  
> [!IMPORTANT]
>  Nie można używać tego interfejsu API w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT, nie są obsługiwane z parametrem /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      int _outp(  
unsigned short port,  
int databyte   
);  
unsigned short _outpw(  
unsigned short port,  
unsigned short dataword   
);  
unsigned long _outpd(  
unsigned short port,  
unsigned long dataword   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 *port*  
 Numer portu.  
  
 *databyte, dataword*  
 Wartości danych wyjściowych.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwracają dane wyjściowe. Nie ma żadnych zwracany błąd.  
  
## <a name="remarks"></a>Uwagi  
 `_outp`, `_outpw`, I `_outpd` funkcje zapisu bajt, word i word o podwójnej precyzji, odpowiednio do portu określonym produktem wyjściowym. *Portu* argument może być liczbą całkowitą bez znaku z zakresu 0 – 65 535; *databyte* może być liczbą całkowitą z zakresu 0 – 255; i *dataword* może mieć dowolną wartość z zakresu całkowitą, krótki całkowitą bez znaku i bez znaku długich liczb całkowitych, odpowiednio.  
  
 Ponieważ te funkcje zapisu bezpośrednio z portem We/Wy, nie można użyć w kodzie użytkownika. Aby uzyskać informacje dotyczące korzystania z portów We/Wy w tych systemach operacyjnych Wyszukaj "Szeregowej komunikacji w Win32" w witrynie MSDN.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_outp`|\<conio.h>|  
|`_outpw`|\<conio.h>|  
|`_outpd`|\<conio.h>|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../c-runtime-library/compatibility.md).  
  
## <a name="libraries"></a>Biblioteki  
 Wszystkie wersje [biblioteki wykonawcze języka C](../c-runtime-library/crt-library-features.md).  
  
## <a name="see-also"></a>Zobacz też  
 [We/Wy konsoli i portu](../c-runtime-library/console-and-port-i-o.md)   
 [_inp, _inpw, _inpd](../c-runtime-library/inp-inpw-inpd.md)