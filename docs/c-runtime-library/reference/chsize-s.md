---
title: "_chsize_s — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _chsize_s
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- chsize_s
- _chsize_s
dev_langs: C++
helpviewer_keywords:
- files [C++], changing size
- chsize_s function
- _chsize_s function
ms.assetid: d88d2e94-6e3b-42a5-8631-16ac4d82fa38
caps.latest.revision: "16"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 3805800a89842ba23d0778a3a5aabf9d60880c38
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="chsizes"></a>_chsize_s
Zmienia rozmiar pliku. To jest wersja [_chsize —](../../c-runtime-library/reference/chsize.md) ulepszeń zabezpieczeń zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
errno_t _chsize_s(   
   int fd,  
   __int64 size   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `fd`  
 Plik deskryptora odwołujących się do otwartego pliku.  
  
 `size`  
 Długość nowego pliku w bajtach.  
  
## <a name="return-value"></a>Wartość zwracana  
 `_chsize_s`Zwraca wartość 0, jeśli rozmiar pliku zostało pomyślnie zmienione. Podano niezerowe wartości zwracanej wskazuje błąd: wartość zwracana jest `EACCES` , jeśli określony plik jest zablokowany przed dostępem, `EBADF` , jeśli określony plik jest tylko do odczytu lub deskryptor jest nieprawidłowa, `ENOSPC` , jeśli nie ma jest wolnego miejsca na urządzeniu lub `EINVAL` Jeśli rozmiar jest mniejszy od zera. `errno`jest ustawiony na tę samą wartość.  
  
 Aby uzyskać więcej informacji na temat tych i innych kody powrotu, zobacz [_doserrno —, errno, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## <a name="remarks"></a>Uwagi  
 `_chsize_s` Funkcja rozszerza lub obcina plik skojarzony z `fd` do długości określonej przez `size`. Plik musi być otwarty w trybie umożliwiającym zapis. Znaki null ('\0') są dołączane, jeśli plik zostanie rozszerzony. Jeśli plik został obcięty, wszystkie dane na końcu pliku skróconą długość oryginalnego pliku zostaną utracone.  
  
 `_chsize_s`Trwa 64-bitową liczbę całkowitą jako rozmiar pliku, a więc może obsługiwać rozmiary plików większych niż 4 GB. `_chsize`jest ograniczone do rozmiarów plików 32-bitowych.  
  
 Ta funkcja weryfikuje jego parametrów. Jeśli `fd` nie jest prawidłowy plik deskryptora lub rozmiar jest mniejszy od zera, zostanie wywołany program obsługi nieprawidłowych parametrów, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md).  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|Opcjonalne nagłówki|  
|-------------|---------------------|---------------------|  
|`_chsize_s`|\<IO.h >|\<errno.h >|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa plików](../../c-runtime-library/file-handling.md)   
 [_chsize —](../../c-runtime-library/reference/chsize.md)   
 [_zamknij](../../c-runtime-library/reference/close.md)   
 [_creat —, _wcreat —](../../c-runtime-library/reference/creat-wcreat.md)   
 [_otwórz, _wopen —](../../c-runtime-library/reference/open-wopen.md)