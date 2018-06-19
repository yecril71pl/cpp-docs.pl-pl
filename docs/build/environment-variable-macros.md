---
title: Makra zmiennych środowiskowych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- NMAKE program, environment variable macros
- environment variables, macros in NMAKE
- macros, environment-variable
ms.assetid: f8e96635-0906-47b0-9f56-12a6fdf5e347
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9ebebb6e7d237746f96c7ac7e27c249244ff825b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32367436"
---
# <a name="environment-variable-macros"></a>Makra zmiennych środowiskowych
NMAKE dziedziczy definicji makra zmiennych środowiskowych, które istnieją przed rozpoczęciem sesji. Jeśli zmienna została ustawiona w środowisku systemu operacyjnego, jest dostępna jako makro NMAKE. Dziedziczony nazwy są konwertowane na wielkie litery. Dziedziczenie występuje przed przetwarzania wstępnego. Opcja /E spowodować makra odziedziczone zmiennych środowiskowych, aby zastąpić makr o takiej samej nazwie w pliku reguł programu make.  
  
 Makra zmiennych środowiskowych można ponownie zdefiniować w sesji i spowoduje to zmianę odpowiednich zmiennej środowiskowej. Można również zmienić zmiennych środowiskowych przy użyciu polecenia SET. Aby zmienić zmienną środowiskową w sesji przy użyciu polecenia SET nie odpowiednie makro, jednak zmienić.  
  
 Na przykład:  
  
```  
PATH=$(PATH);\nonesuch  
  
all:  
    echo %PATH%  
```  
  
 W tym przykładzie zmiana `PATH` zmiany odpowiednich zmiennej środowiskowej `PATH`; dołącza `\nonesuch` do ścieżki.  
  
 Jeśli zmienna środowiskowa jest zdefiniowany jako ciąg, który jest nieprawidłowy w pliku reguł programu make, makro nie jest tworzony, i jest generowany bez ostrzeżenia. Jeśli wartość zmiennej zawiera znak dolara ($), NMAKE zinterpretuje ją jako początku wywołanie makra. Użycie makra może spowodować nieoczekiwane zachowanie.  
  
## <a name="see-also"></a>Zobacz też  
 [Specjalne makra NMAKE](../build/special-nmake-macros.md)