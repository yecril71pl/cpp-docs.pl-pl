---
title: "_open_osfhandle — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _open_osfhandle
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
- _open_osfhandle
- open_osfhandle
dev_langs: C++
helpviewer_keywords:
- open_osfhandle function
- file handles [C++], associating
- _open_osfhandle function
ms.assetid: 30d94df4-7868-4667-a401-9eb67ecb7855
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 8d214df5d1e1cd3a48336723cecbf530402eafe3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="openosfhandle"></a>_open_osfhandle
Powoduje skojarzenie deskryptora pliku wykonawcze języka C z istniejących dojście do pliku systemu operacyjnego.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      int _open_osfhandle (  
   intptr_t osfhandle,  
   int flags   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `osfhandle`  
 Dojście do pliku systemu operacyjnego.  
  
 `flags`  
 Typy operacji dozwolone.  
  
## <a name="return-value"></a>Wartość zwracana  
 W przypadku powodzenia `_open_osfhandle` zwraca deskryptor pliku wykonawcze języka C. W przeciwnym razie zwraca wartość -1.  
  
## <a name="remarks"></a>Uwagi  
 `_open_osfhandle` Funkcja przydziela deskryptora pliku wykonawcze języka C i kojarzy ją z określonego przez dojście do pliku systemu operacyjnego `osfhandle`. `flags` Argument jest wyrażeniem liczby całkowitej z co najmniej jednego z manifestu stałe zdefiniowane w Fcntl.h. Gdy dwa lub więcej manifestu stałe są używane do formularza `flags` argumentu, stałe są łączone z operator Alternatywy ( **&#124;** ).  
  
 Fcntl.h definiuje następujące stałe manifestu.  
  
 **_O_APPEND —**  
 Określa położenie pliku wskaźnik na koniec pliku przed każdej operacji zapisu.  
  
 **_O_RDONLY —**  
 Otwiera plik tylko odczytywanie.  
  
 **_O_TEXT —**  
 Otwiera plik w trybie tekstowym (translacji).  
  
 **_O_WTEXT**  
 Otwiera plik w trybie Unicode (przetłumaczonego UTF-16).  
  
 Można zamknąć pliku, która została otwarta z `_open_osfhandle`, wywołaj `_close`. Dojście podstawowych jest również zamknięte przez wywołanie do `_close`, więc nie jest konieczne do wywołania funkcji Win32 `CloseHandle` w dojściu do oryginalnego.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_open_osfhandle`|\<IO.h >|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="libraries"></a>Biblioteki  
 Wszystkie wersje [biblioteki wykonawcze języka C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa plików](../../c-runtime-library/file-handling.md)