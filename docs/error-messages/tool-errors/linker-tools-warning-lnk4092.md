---
title: Ostrzeżenie LNK4092 narzędzi konsolidatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4092
dev_langs:
- C++
helpviewer_keywords:
- LNK4092
ms.assetid: d569ec47-a338-40e1-940b-8a8061459acb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 72edd9e75dbc781355396e38f767a64c1ded3aa9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
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