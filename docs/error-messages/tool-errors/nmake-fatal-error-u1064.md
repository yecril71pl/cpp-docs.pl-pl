---
title: Błąd krytyczny NMAKE U1064
ms.date: 11/04/2016
f1_keywords:
- U1064
helpviewer_keywords:
- U1064
ms.assetid: 7141e66e-cde6-4173-84df-a391f3ebcdd1
ms.openlocfilehash: bfc42c458c1932287f17f367d09c4b23c2c201a4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80182828"
---
# <a name="nmake-fatal-error-u1064"></a>Błąd krytyczny NMAKE U1064

Nie znaleziono pliku reguł programu make i nie określono elementu docelowego

W wierszu polecenia NMAKE nie określono pliku reguł programu make lub elementu docelowego, a bieżący katalog nie zawiera plik o nazwie make.

NMAKE wymaga pliku reguł programu make lub wiersza polecenia (lub obu tych opcji). Aby udostępnić plik reguł programu make NMAKE, należy określić opcję/F lub umieścić w bieżącym katalogu pliku o nazwie reguł programu make. NMAKE może utworzyć obiekt docelowy wiersza polecenia za pomocą reguły wnioskowania, jeśli nie podano pliku reguł programu make.
