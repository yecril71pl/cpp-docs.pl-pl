---
title: "_mbcjistojms —, _mbcjistojms_l —, _mbcjmstojis —, _mbcjmstojis_l — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _mbcjistojms
- _mbcjmstojis
- _mbcjistojms_l
- _mbcjmstojis_l
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
- mbcjistojms
- _mbcjistojms
- _mbcjistojms_l
- _mbcjmstojis_l
- _mbcjmstojis
- mbcjmstojis_l
- mbcjistojms_l
- mbcjmstojis
dev_langs: C++
helpviewer_keywords:
- _mbcjmstojis_l function
- _mbcjistojms function
- mbcjmstojis function
- _mbcjistojms_l function
- _mbcjmstojis function
- mbcjistojms function
- mbcjmstojis_l function
- mbcjistojms_l function
ms.assetid: dece5127-b337-40a4-aa10-53320a2c9432
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3ed3aada11b5020c285ce9fb867f08b288055581
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="mbcjistojms-mbcjistojmsl-mbcjmstojis-mbcjmstojisl"></a>_mbcjistojms, _mbcjistojms_l, _mbcjmstojis, _mbcjmstojis_l
Wykonuje konwersję między znakami Japonii branżowy Standard (JIS) i Microsoft Japonii (JMS).  
  
> [!IMPORTANT]
>  Nie można używać tego interfejsu API w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT, nie są obsługiwane z parametrem /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Składnia  
  
```  
unsigned int _mbcjistojms(  
   unsigned int c   
);  
unsigned int _mbcjistojms_l(  
   unsigned int c,  
   _locale_t locale  
);  
unsigned int _mbcjmstojis(  
   unsigned int c   
);  
unsigned int _mbcjmstojis_l(  
   unsigned int c,  
   _locale_t locale  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `c`  
 Znak do konwersji.  
  
 `local`  
 Ustawienia regionalne do użycia.  
  
## <a name="return-value"></a>Wartość zwracana  
 W japońskich ustawień regionalnych te funkcje zwraca znak przekonwertowany lub zwraca 0, jeśli konwersja nie jest możliwe. Na ustawień regionalnych innych niż japońska te funkcje zwracają znaków przekazany.  
  
## <a name="remarks"></a>Uwagi  
 `_mbcjistojms` Funkcja konwertuje znak Japonii branżowy Standard (JIS) znaków Kanji firmy Microsoft (Shift JIS). Znak jest konwertowana tylko wtedy, gdy bajtów potencjalnych klientów i dziennika znajdują się w zakresie 0x21 - 0x7E. Jeśli poza tym zakresem realizacji lub wersji próbnej bajt `errno` ma ustawioną wartość `EILSEQ`. Aby uzyskać więcej informacji dotyczących tego i innych kodów błędów, zobacz [errno _doserrno —, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
 `_mbcjmstojis` Funkcja konwertuje znaków Shift JIS znaków JIS. Znak jest konwertowana tylko wtedy, gdy bajtu znajduje się w zakresie 0x81-0x9F lub wartość 0xE0 - 0xFC i bajt jest w zasięgu 0x40-0x7E lub 0x80 - 0xFC. Należy pamiętać, że niektóre kodu wskazuje z tego zakresu nie ma przypisany znak w związku z czym nie można przekonwertować.  
  
 Wartość `c` powinna być 16-bitową wartość, którego górny 8 bitów reprezentują bajtu znaku do przekonwertowania i którego pierwszych 8 bitów reprezentują bajt.  
  
 Wartość wyjściowa jest zagrożony ustawienie `LC_CTYPE` ustawienie kategorii ustawień regionalnych; zobacz [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md) Aby uzyskać więcej informacji. Wersje tych funkcji bez `_l` Użyj sufiksu bieżące ustawienia regionalne tego zachowania zależnych od ustawień regionalnych; wersje z `_l` sufiks są identyczne, z wyjątkiem tego, aby były używane zamiast przekazany parametr ustawień regionalnych. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).  
  
 We wcześniejszych wersjach `_mbcjistojms` i `_mbcjmstojis` były nazywane `jistojms` i `jmstojis`odpowiednio. `_mbcjistojms`, `_mbcjistojms_l`, `_mbcjmstojis` i `_mbcjmstojis_l` należy użyć.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_mbcjistojms`|\<mbstring.h >|  
|`_mbcjistojms_l`|\<mbstring.h >|  
|`_mbcjmstojis`|\<mbstring.h >|  
|`_mbcjmstojis_l`|\<mbstring.h >|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Konwersja danych](../../c-runtime-library/data-conversion.md)   
 [_ismbb, procedury](../../c-runtime-library/ismbb-routines.md)