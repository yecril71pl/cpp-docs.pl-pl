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
ms.openlocfilehash: 4240bf2c553957e73d5ead0bdd03ea129450645b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46093002"
---
# <a name="nmake-fatal-error-u1064"></a>Błąd krytyczny NMAKE U1064

Nie znaleziono polecenia MAKEFILE i nie określono elementu docelowego

W wierszu polecenia NMAKE nie określono pliku reguł programu make lub obiektu docelowego, a bieżący katalog nie zawiera plik o nazwie pliku reguł programu MAKE.

NMAKE wymaga pliku reguł programu make lub wiersza polecenia docelowego (lub obu). Aby udostępnić pliku reguł programu make NMAKE, określ opcję /F albo umieścić plik o nazwie pliku reguł programu MAKE w bieżącym katalogu. NMAKE można utworzyć obiektu docelowego wiersza polecenia przy użyciu reguły wnioskowania, jeśli nie podano pliku reguł programu make.