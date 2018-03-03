---
title: "Błąd krytyczny NMAKE U1064 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- U1064
dev_langs:
- C++
helpviewer_keywords:
- U1064
ms.assetid: 7141e66e-cde6-4173-84df-a391f3ebcdd1
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 20b6c767145176c459d0b70d96842223218cd0b2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="nmake-fatal-error-u1064"></a>Błąd krytyczny NMAKE U1064
Nie znaleziono polecenia MAKEFILE i nie określono elementu docelowego  
  
 W wierszu polecenia NMAKE nie określono pliku reguł programu make lub element docelowy, a bieżący katalog nie zawiera plik o nazwie pliku reguł programu MAKE.  
  
 NMAKE wymaga pliku reguł programu make lub element docelowy wiersza polecenia (lub obie). Aby udostępnić pliku reguł programu make NMAKE, określ opcję /F lub umieścić plik o nazwie pliku reguł programu MAKE w bieżącym katalogu. NMAKE można utworzyć obiektu docelowego wiersza polecenia przy użyciu reguły wnioskowania, jeśli nie podano pliku reguł programu make.