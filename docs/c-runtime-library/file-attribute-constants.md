---
title: "Stałe atrybutów pliku | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- A_HIDDEN
- _A_NORMAL
- _A_SUBDIR
- _A_RDONLY
- A_NORMAL
- A_SUBDIR
- _A_SYSTEM
- c.constants.file
- _A_HIDDEN
- A_RDONLY
- _A_ARCH
- A_ARCH
dev_langs: C++
helpviewer_keywords:
- constants [C++], file attributes
- file attribute constants [C++]
- _A_SYSTEM constant
- files [C++], file attribute constants
- _A_SUBDIR constant
- _A_ARCH constant
- _A_NORMAL constant
- _A_HIDDEN constant
- _A_RDONLY constant
ms.assetid: 8dc8ccb9-99f5-446b-876c-7ebecc2f764f
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 55dc7b0c0c21c8ee149e4be8eb829de29d73aacd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="file-attribute-constants"></a>Stałe atrybutów pliku
## <a name="syntax"></a>Składnia  
  
```  
  
#include <io.h>  
```  
  
## <a name="remarks"></a>Uwagi  
 Te stałe są określane atrybuty bieżącego pliku lub katalogu określonym przez funkcję.  
  
 Atrybuty są reprezentowane przez następujących stałych manifestu:  
  
 `_A_ARCH`  
 Archiwum. Zestaw zawsze, gdy plik jest zmienione i wyczyszczone za pomocą polecenia tworzenia kopii zapasowej. Wartość: wartości 0x20  
  
 `_A_HIDDEN`  
 Plik ukryty. Zwykle widoczne polecenie DIR, chyba że używana jest opcja /AH. Zwraca informacje o normalne pliki, a także pliki z tym atrybutem. Wartość: 0x02  
  
 `_A_NORMAL`  
 Normalny. Plik można odczytać lub zapisywane bez ograniczeń. Wartość: 0x00  
  
 `_A_RDONLY`  
 Tylko do odczytu. Nie można otworzyć pliku do zapisu i nie można utworzyć pliku o tej samej nazwie. Wartość: 0x01  
  
 `_A_SUBDIR`  
 Podkatalog. Wartość: 0x10  
  
 `_A_SYSTEM`  
 System plików. Zwykle widoczne polecenie DIR, chyba że używana jest opcja /AS. Wartość: 0x04  
  
 Wiele stałych można łączyć z operatora OR (&#124;).  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje wyszukiwania nazwy pliku](../c-runtime-library/filename-search-functions.md)   
 [Stałe globalne](../c-runtime-library/global-constants.md)