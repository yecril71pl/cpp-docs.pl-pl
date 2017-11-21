---
title: "_inp —, _inpw —, _inpd — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _inp
- _inpw
- _inpd
apilocation:
- msvcrt.dll
- msvcr120.dll
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcr80.dll
- msvcr100.dll
- msvcr90.dll
apitype: DLLExport
f1_keywords:
- inpd
- _inp
- _inpw
- _inpd
dev_langs: C++
helpviewer_keywords:
- inp function
- inpw function
- ports, I/O routines
- inpd function
- _inp function
- _inpd function
- I/O [CRT], port
- _inpw function
ms.assetid: 5d9c2e38-fc85-4294-86d5-7282cc02d1b3
caps.latest.revision: "16"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 983efc1f3341ca334415e8cdd37f96f12fbb3e11
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="inp-inpw-inpd"></a>_inp, _inpw, _inpd
Dane wejściowe z portu, byte (`_inp`), wyraz (`_inpw`), lub word o podwójnej precyzji (`_inpd`).  
  
> [!IMPORTANT]
>  Te funkcje są przestarzałe. Począwszy od programu Visual Studio 2015, ich nie są dostępne w CRT.  
  
> [!IMPORTANT]
>  Nie można używać tego interfejsu API w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT, nie są obsługiwane z parametrem /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Składnia  
  
```  
int _inp(   
   unsigned short port   
);  
unsigned short _inpw(   
   unsigned short port   
);  
unsigned long _inpd(   
   unsigned short port   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `port`  
 Numer portu We/Wy.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwracają byte, word, lub słowa podwójne odczytywać `port`. Nie ma żadnych zwracany błąd.  
  
## <a name="remarks"></a>Uwagi  
 `_inp`, `_inpw`, I `_inpd` funkcje odczytywać bajt, word i word o podwójnej precyzji, odpowiednio, określony port wejściowy. Wartość wejściowa można żadnych krótkich liczbę całkowitą bez znaku z zakresu 0 – 65 535.  
  
 Ponieważ te funkcje odczytu bezpośrednio z portem We/Wy, ich nie mogą być używane w kodzie użytkownika w systemie Windows NT, Windows 2000, Windows XP i Windows Server 2003.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_inp`|\<conio.h >|  
|`_inpw`|\<conio.h >|  
|`_inpd`|\<conio.h >|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../c-runtime-library/compatibility.md).  
  
## <a name="libraries"></a>Biblioteki  
 Wszystkie wersje [biblioteki wykonawcze języka C](../c-runtime-library/crt-library-features.md).  
  
## <a name="see-also"></a>Zobacz też  
 [We/Wy konsoli i portu](../c-runtime-library/console-and-port-i-o.md)   
 [_outp —, _outpw —, _outpd —](../c-runtime-library/outp-outpw-outpd.md)