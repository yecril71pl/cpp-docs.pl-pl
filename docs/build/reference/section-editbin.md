---
title: -SECTION (POLECENIA EDITBIN) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /section
dev_langs:
- C++
helpviewer_keywords:
- -SECTION editbin option
- SECTION editbin option
- alignment characters in sections
- /SECTION editbin option
ms.assetid: 4680ab4e-c984-4251-8241-93440cad7615
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e29e258b4fb661cfa06e057704bba983ad924f34
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="section-editbin"></a>/SECTION (EDITBIN)
```  
/SECTION:name[=newname][,attributes][alignment]  
```  
  
## <a name="remarks"></a>Uwagi  
 Ta opcja zmienia atrybuty sekcji, zastępując atrybuty, które zostały określone, gdy plik obiektu dla sekcji został skompilowany lub połączone.  
  
 Po dwukropkiem ( **:** ), określ *nazwa* sekcji. Aby zmienić nazwę sekcji, wykonaj *nazwa* znakiem równości (=) i *newname* dla sekcji.  
  
 Ustawianie lub zmienianie sekcji `attributes`, określ przecinka (**,**) następuje co najmniej jeden znak atrybutów. Aby odwrócić atrybutu, należy poprzedzić jej znak symbolem wykrzyknika (!). Następujące znaki Określ atrybuty pamięci:  
  
|Atrybut|Ustawienie|  
|---------------|-------------|  
|c|kod|  
|d|Discardable|  
|e|pliku wykonywalnego|  
|mogę|danymi zainicjowanymi|  
|K|pamięci podręcznej pamięci wirtualnej|  
|m|Usuń Link|  
|o|informacje o łączu|  
|p|stronicowania pamięci wirtualnej|  
|r|przeczytaj|  
|s|udostępnione|  
|u|niezainicjowanych danych|  
|w|pisz|  
  
 Do sterowania *wyrównanie*, określ znak **A** jednego z następujących znaków rozmiar można ustawić wyrównania w bajtach, w następujący sposób:  
  
|Znak|Wyrównanie rozmiar w bajtach|  
|---------------|-----------------------------|  
|1|1|  
|2|2|  
|4|4|  
|8|8|  
|p|16|  
|t|32|  
|s|64|  
|x|brak wyrównania|  
  
 Określ `attributes` i *wyrównanie* znaków w postaci ciągu z żadnego wolnego miejsca. Znaki nie jest uwzględniana wielkość liter.  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje EDITBIN](../../build/reference/editbin-options.md)