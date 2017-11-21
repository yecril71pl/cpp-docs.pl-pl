---
title: "_commit — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _commit
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
- _commit
- commit
dev_langs: C++
helpviewer_keywords:
- files [C++], flushing
- flushing files to disk
- commit function
- _commit function
- committing files to disk
ms.assetid: d0c74d3a-4f2d-4fb0-b140-2d687db3d233
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 4df750e90ccd36545348f765ecd00e02728481e2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="commit"></a>_commit
Liczba opróżnień pliku bezpośrednio na dysku.  
  
## <a name="syntax"></a>Składnia  
  
```  
int _commit(   
   int fd   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `fd`  
 Plik deskryptora odwołujących się do otwartego pliku.  
  
## <a name="return-value"></a>Wartość zwracana  
 `_commit`Zwraca wartość 0, jeśli plik został pomyślnie wyczyszczone na dysku. Zwracana wartość -1 wskazuje błąd.  
  
## <a name="remarks"></a>Uwagi  
 `_commit` Funkcja wymusza systemu operacyjnego można zapisać pliku skojarzone z `fd` na dysku. To wywołanie gwarantuje, że określony plik jest opróżniany natychmiast, nie uznania systemu operacyjnego.  
  
 Jeśli `fd` jest deskryptora nieprawidłowy plik wywołany program obsługi nieprawidłowych parametrów, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może kontynuować, funkcja zwraca wartość -1 i `errno` ma ustawioną wartość `EBADF`.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|Opcjonalne nagłówki|  
|-------------|---------------------|----------------------|  
|`_commit`|\<IO.h >|\<errno.h >|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="see-also"></a>Zobacz też  
 [We/Wy niskiego poziomu](../../c-runtime-library/low-level-i-o.md)   
 [_creat —, _wcreat —](../../c-runtime-library/reference/creat-wcreat.md)   
 [_otwórz, _wopen —](../../c-runtime-library/reference/open-wopen.md)   
 [_przeczytaj](../../c-runtime-library/reference/read.md)   
 [_Write](../../c-runtime-library/reference/write.md)