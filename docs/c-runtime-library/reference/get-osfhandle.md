---
title: "_get_osfhandle — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 09/11/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _get_osfhandle
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
- get_osfhandle
- _get_osfhandle
dev_langs: C++
helpviewer_keywords:
- operating systems, getting file handles
- get_osfhandle function
- _get_osfhandle function
- file handles [C++], operating system
ms.assetid: 0bdd728a-4fd8-410b-8c9f-01a121135196
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 4e3b15b4577d1d8c0b24df82acff76494474c4e6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="getosfhandle"></a>_get_osfhandle

Pobiera dojście do pliku systemu operacyjnego skojarzonego z deskryptorem określonego pliku.  
  
## <a name="syntax"></a>Składnia  
  
```  
intptr_t _get_osfhandle(   
   int fd   
);  
```  
  
### <a name="parameters"></a>Parametry

*FD* istniejącego pliku deskryptora.  
  
## <a name="return-value"></a>Wartość zwracana

Dojście do pliku systemu operacyjnego Jeśli *fd* jest nieprawidłowy. W przeciwnym razie program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, ta funkcja zwraca `INVALID_HANDLE_VALUE` (-1) i ustawia `errno` do `EBADF`, wskazując nieprawidłowe dojście do pliku.  
  
## <a name="remarks"></a>Uwagi

Aby zamknąć plik, którego dojście do pliku systemu operacyjnego są uzyskiwane przez `_get_osfhandle`, wywołaj [ \_zamknąć](../../c-runtime-library/reference/close.md) na deskryptorów plików *fd*. Dojście podstawowych jest również zamknięte przez wywołanie do `_close`, więc nie jest konieczne do wywołania funkcji Win32 `CloseHandle` w dojściu do oryginalnego.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_get_osfhandle`|\<IO.h >|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="see-also"></a>Zobacz też

[Obsługa plików](../../c-runtime-library/file-handling.md)   
[_zamknij](../../c-runtime-library/reference/close.md)   
[_creat —, _wcreat —](../../c-runtime-library/reference/creat-wcreat.md)   
[_dup —, _dup2 —](../../c-runtime-library/reference/dup-dup2.md)   
[_otwórz, _wopen —](../../c-runtime-library/reference/open-wopen.md)
