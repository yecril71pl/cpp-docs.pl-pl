---
title: Błąd krytyczny NMAKE U1064 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1064
dev_langs:
- C++
helpviewer_keywords:
- U1064
ms.assetid: 7141e66e-cde6-4173-84df-a391f3ebcdd1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e5573943fc2c274d48768933a634b2c052361a8f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33332143"
---
# <a name="nmake-fatal-error-u1064"></a>Błąd krytyczny NMAKE U1064
Nie znaleziono polecenia MAKEFILE i nie określono elementu docelowego  
  
 W wierszu polecenia NMAKE nie określono pliku reguł programu make lub element docelowy, a bieżący katalog nie zawiera plik o nazwie pliku reguł programu MAKE.  
  
 NMAKE wymaga pliku reguł programu make lub element docelowy wiersza polecenia (lub obie). Aby udostępnić pliku reguł programu make NMAKE, określ opcję /F lub umieścić plik o nazwie pliku reguł programu MAKE w bieżącym katalogu. NMAKE można utworzyć obiektu docelowego wiersza polecenia przy użyciu reguły wnioskowania, jeśli nie podano pliku reguł programu make.