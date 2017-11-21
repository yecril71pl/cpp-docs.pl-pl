---
title: "Ostrzeżenie LNK4092 narzędzi konsolidatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK4092
dev_langs: C++
helpviewer_keywords: LNK4092
ms.assetid: d569ec47-a338-40e1-940b-8a8061459acb
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 3771cfc08a091a796e67e8c11a16c842e6a4346a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="linker-tools-warning-lnk4092"></a>Ostrzeżenie LNK4092 narzędzi konsolidatora
współużytkowana, zapisywalna sekcja "sekcji" zawiera relokacje; Obraz może nie działać poprawnie  
  
 Konsolidator emituje to ostrzeżenie, gdy mają współdzielonej sekcji, aby ostrzec o potencjalnie poważny problem.  
  
 Jednym ze sposobów udostępniania danych między wieloma procesami jest oznaczenie sekcji jako "udostępnione". Jednak oznaczenie sekcji jako udostępniony mogą powodować problemy. Na przykład masz bibliotekę DLL, która zawiera deklaracje podobny do tego w sekcji udostępnionych danych:  
  
```  
int var = 1;  
int *pvar = &var;  
```  
  
 Nie można rozpoznać konsolidator `pvar` , ponieważ jej wartość zależy od tego, gdzie plik DLL, który jest ładowany w pamięci, dlatego umieszcza rekord relokacji w bibliotece DLL. Gdy plik DLL, który jest ładowany do pamięci, adres `var` można rozwiązać ten problem i `pvar` przypisane. Jeśli inny proces ładuje bibliotekę DLL tego samego, ale nie można załadować w taki sam adres, relokacji dla adresu `var` zostaną zaktualizowane dla drugiego proces i przestrzeń adresowa procesu pierwszy wskaże niewłaściwy adres.