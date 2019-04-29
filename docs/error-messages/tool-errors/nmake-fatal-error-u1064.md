---
title: Błąd krytyczny NMAKE U1064
ms.date: 11/04/2016
f1_keywords:
- U1064
helpviewer_keywords:
- U1064
ms.assetid: 7141e66e-cde6-4173-84df-a391f3ebcdd1
ms.openlocfilehash: 71213391032989e5faf8889761b29194928125a0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62367411"
---
# <a name="nmake-fatal-error-u1064"></a>Błąd krytyczny NMAKE U1064

Nie znaleziono polecenia MAKEFILE i nie określono elementu docelowego

W wierszu polecenia NMAKE nie określono pliku reguł programu make lub obiektu docelowego, a bieżący katalog nie zawiera plik o nazwie pliku reguł programu MAKE.

NMAKE wymaga pliku reguł programu make lub wiersza polecenia docelowego (lub obu). Aby udostępnić pliku reguł programu make NMAKE, określ opcję /F albo umieścić plik o nazwie pliku reguł programu MAKE w bieżącym katalogu. NMAKE można utworzyć obiektu docelowego wiersza polecenia przy użyciu reguły wnioskowania, jeśli nie podano pliku reguł programu make.