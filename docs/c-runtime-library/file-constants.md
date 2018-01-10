---
title: "Stałe pliku | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _O_EXCL
- _O_RDWR
- _O_APPEND
- _O_RDONLY
- _O_TRUNC
- _O_CREAT
- _O_WRONLY
dev_langs: C++
helpviewer_keywords:
- _O_RDWR constant
- O_EXCL constant
- O_RDWR constant
- O_WRONLY constant
- O_APPEND constant
- O_CREAT constant
- _O_CREAT constant
- _O_APPEND constant
- _O_EXCL constant
- O_TRUNC constant
- _O_RDONLY constant
- _O_TRUNC constant
- O_RDONLY constant
- _O_WRONLY constant
ms.assetid: c8fa5548-9ac2-4217-801d-eb45e86f2fa4
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 59e108f8674b002cdbc5e7ab0b9c1868eea632df
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="file-constants"></a>Plik — Stałe
## <a name="syntax"></a>Składnia  
  
```  
  
#include <fcntl.h>  
  
```  
  
## <a name="remarks"></a>Uwagi  
 Wyrażenie całkowite sformułowanych z jednego lub więcej te stałe Określa typ odczytu lub zapisu operacji dozwolone. Jest on tworzony przez połączenie co najmniej jedną stałą ze stałą tryb tłumaczenia.  
  
 Plik — stałe są następujące:  
  
 `_O_APPEND`  
 Zmienia położenie wskaźnika pliku na koniec pliku przed każdej operacji zapisu.  
  
 `_O_CREAT`  
 Tworzy i otwiera nowy plik do zapisu; to ustawienie nie działa, jeśli plik określony przez *filename* istnieje.  
  
 `_O_EXCL`  
 Zwraca wartość błędu, jeśli plik określony przez *filename* istnieje. Ma zastosowanie tylko w przypadku użycia z `_O_CREAT`.  
  
 `_O_RDONLY`  
 Otwiera plik do odczytu. Jeśli ta flaga nie zostanie podany, ani `_O_RDWR` ani `_O_WRONLY` można przydzielić.  
  
 `_O_RDWR`  
 Otwiera plik do odczytywanie i zapisywanie; Jeśli ta flaga nie zostanie podany, ani `_O_RDONLY` ani `_O_WRONLY` można przydzielić.  
  
 `_O_TRUNC`  
 Otwiera i obcina istniejący plik na zero length; Plik musi mieć uprawnienia do zapisu. Zawartość pliku zostaną zniszczone. Jeśli ta flaga jest podany, nie można określić `_O_RDONLY`.  
  
 `_O_WRONLY`  
 Otwiera plik do zapisu. Jeśli ta flaga nie zostanie podany, ani `_O_RDONLY` ani `_O_RDWR` można przydzielić.  
  
## <a name="see-also"></a>Zobacz też  
 [_otwórz, _wopen —](../c-runtime-library/reference/open-wopen.md)   
 [_sopen —, _wsopen —](../c-runtime-library/reference/sopen-wsopen.md)   
 [Stałe globalne](../c-runtime-library/global-constants.md)