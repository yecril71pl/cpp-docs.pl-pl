---
title: "_putch —, _putwch — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _putwch
- _putch
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
- api-ms-win-crt-conio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _putch
- putwch
- _putwch
dev_langs: C++
helpviewer_keywords:
- _putch function
- characters, writing
- putwch function
- _putwch function
- putch function
- console, writing characters to
ms.assetid: 3babc7cf-e333-405d-8449-c788d61d51aa
caps.latest.revision: "19"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 74a864aba662d17a5b69d6cc0bdaf6f260e15872
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="putch-putwch"></a>_putch, _putwch
Zapisuje znak do konsoli.  
  
> [!IMPORTANT]
>  Nie można używać tego interfejsu API w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT, nie są obsługiwane z parametrem /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      int _putch(  
int c   
);  
wint_t _putwch(  
   wchar_t c  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `c`  
 Znak jako dane wyjściowe.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca `c` w przypadku powodzenia. Jeśli `_putch` nie powiedzie się, zwraca `EOF`; Jeśli **_putwch —** nie powiedzie się, zwraca **weof —**.  
  
## <a name="remarks"></a>Uwagi  
 Te funkcje wpisz znak `c` bezpośrednio, bez buforowania do konsoli. W systemie Windows NT **_putwch —** zapisuje znaków Unicode przy użyciu bieżących ustawień regionalnych konsoli.  
  
 Wersje z **_nolock —** sufiks są identyczne z tą różnicą, że nie są chronione przez inne wątki od zakłóceń. Aby uzyskać więcej informacji, zobacz `_putch_nolock`, `_putwch_nolock`.  
  
### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu  
  
|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|**_puttch**|`_putch`|`_putch`|**_putwch —**|  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_putch`|\<conio.h >|  
|**_putwch —**|\<conio.h >|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="libraries"></a>Biblioteki  
 Wszystkie wersje [biblioteki wykonawcze języka C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="example"></a>Przykład  
 Zobacz przykład [_getch —](../../c-runtime-library/reference/getch-getwch.md).  
  
## <a name="see-also"></a>Zobacz też  
 [We/Wy konsoli i portu](../../c-runtime-library/console-and-port-i-o.md)   
 [_cprintf —, _cprintf_l —, _cwprintf — _cwprintf_l —](../../c-runtime-library/reference/cprintf-cprintf-l-cwprintf-cwprintf-l.md)   
 [_getch —, _getwch —](../../c-runtime-library/reference/getch-getwch.md)