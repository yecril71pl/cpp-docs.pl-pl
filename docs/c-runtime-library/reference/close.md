---
title: _zamknij | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _close
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
f1_keywords: _close
dev_langs: C++
helpviewer_keywords:
- _close function
- close function
- files [C++], closing
ms.assetid: 4708a329-8acf-4cd9-b7b0-a952e1897247
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2cb1cace610479113c3a4be00daf634b0da75e2c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="close"></a>_close
Zamyka plik.  
  
## <a name="syntax"></a>Składnia  
  
```  
int _close(   
   int fd   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `fd`  
 Plik deskryptora odwołujących się do otwartego pliku.  
  
## <a name="return-value"></a>Wartość zwracana  
 `_close`Zwraca wartość 0, jeśli plik został zamknięty pomyślnie. Zwracana wartość -1 wskazuje błąd.  
  
## <a name="remarks"></a>Uwagi  
 `_close` Funkcja zamyka plik skojarzony z `fd`.  
  
 Deskryptorów plików i dojście do pliku podstawowego systemu operacyjnego są zamknięte. W związku z tym nie jest konieczne do wywołania `CloseHandle` Jeśli plik został pierwotnie otwarty przy użyciu funkcji Win32 `CreateFile` i przekonwertować deskryptora pliku przy użyciu `_open_osfhandle`.  
  
 Ta funkcja weryfikuje jego parametrów. Jeśli `fd` deskryptor nieprawidłowego pliku, program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli dozwolone jest wykonywanie aby kontynuować, funkcje, zwraca -1 i `errno` ma ustawioną wartość `EBADF`.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|Opcjonalne nagłówki|  
|-------------|---------------------|---------------------|  
|`_close`|\<IO.h >|\<errno.h >|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="example"></a>Przykład  
 Zobacz przykład [_otwórz](../../c-runtime-library/reference/open-wopen.md).  
  
## <a name="see-also"></a>Zobacz też  
 [We/Wy niskiego poziomu](../../c-runtime-library/low-level-i-o.md)   
 [_chsize —](../../c-runtime-library/reference/chsize.md)   
 [_creat —, _wcreat —](../../c-runtime-library/reference/creat-wcreat.md)   
 [_dup —, _dup2 —](../../c-runtime-library/reference/dup-dup2.md)   
 [_otwórz, _wopen —](../../c-runtime-library/reference/open-wopen.md)   
 [_unlink, _wunlink](../../c-runtime-library/reference/unlink-wunlink.md)