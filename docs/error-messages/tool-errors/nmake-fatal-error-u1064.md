---
title: "Błąd krytyczny NMAKE U1064 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: U1064
dev_langs: C++
helpviewer_keywords: U1064
ms.assetid: 7141e66e-cde6-4173-84df-a391f3ebcdd1
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 123b84922df702aad9dc391da1b83bfa81265fe0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="nmake-fatal-error-u1064"></a>Błąd krytyczny NMAKE U1064
Nie znaleziono polecenia MAKEFILE i nie określono elementu docelowego  
  
 W wierszu polecenia NMAKE nie określono pliku reguł programu make lub element docelowy, a bieżący katalog nie zawiera plik o nazwie pliku reguł programu MAKE.  
  
 NMAKE wymaga pliku reguł programu make lub element docelowy wiersza polecenia (lub obie). Aby udostępnić pliku reguł programu make NMAKE, określ opcję /F lub umieścić plik o nazwie pliku reguł programu MAKE w bieżącym katalogu. NMAKE można utworzyć obiektu docelowego wiersza polecenia przy użyciu reguły wnioskowania, jeśli nie podano pliku reguł programu make.