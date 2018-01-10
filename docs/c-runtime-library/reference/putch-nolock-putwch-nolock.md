---
title: "_putch_nolock —, _putwch_nolock — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _putwch_nolock
- _putch_nolock
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
- _putch_nolock
- _puttch_nolock
- putch_nolock
- putwch_nolock
- _putwch_nolock
dev_langs: C++
helpviewer_keywords:
- putwch_nolock function
- puttch_nolock function
- characters, writing
- putch_nolock function
- _putch_nolock function
- _puttch_nolock function
- console, writing characters to
- _putwch_nolock function
ms.assetid: edbc811d-bac6-47fa-a872-fe4f3a1590b0
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9589b1f658ac7746fbb8947b871a3f81823e6826
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="putchnolock-putwchnolock"></a>_putch_nolock, _putwch_nolock
Zapisuje znak do konsoli bez blokowania wątku.  
  
> [!IMPORTANT]
>  Nie można używać tego interfejsu API w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT, nie są obsługiwane z parametrem /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      int _putch_nolock(  
int c  
);  
wint_t _putwch_nolock(  
wchar_t c  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 *c*  
 Znak jako dane wyjściowe.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca *c* w przypadku powodzenia. Jeśli **_putch_nolock —** nie powiedzie się, zwraca **EOF**; Jeśli **_putwch_nolock —** nie powiedzie się, zwraca **weof —**.  
  
## <a name="remarks"></a>Uwagi  
 **_putch_nolock —** i **_putwch_nolock —** są takie same jak **_putch —** i **_putwch —**odpowiednio z tą różnicą, że nie są chronione z zakłócenia przez inne wątki. Może być szybsze, ponieważ nie wiążą się z obciążenie zablokowania inne wątki. Ich używać tylko w kontekstach wątkowo, np. aplikacje jednowątkowe lub gdzie wywoływania zakres już obsługuje izolacji wątku.  
  
### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu  
  
|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|**_puttch_nolock —**|**_putch_nolock —**|**_putch_nolock —**|**_putwch_nolock —**|  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|**_putch_nolock —**|\<conio.h >|  
|**_putwch_nolock —**|\<conio.h >|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="libraries"></a>Biblioteki  
 Wszystkie wersje [biblioteki wykonawcze języka C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="see-also"></a>Zobacz też  
 [We/Wy konsoli i portu](../../c-runtime-library/console-and-port-i-o.md)   
 [_cprintf —, _cprintf_l —, _cwprintf — _cwprintf_l —](../../c-runtime-library/reference/cprintf-cprintf-l-cwprintf-cwprintf-l.md)   
 [_getch, _getwch](../../c-runtime-library/reference/getch-getwch.md)