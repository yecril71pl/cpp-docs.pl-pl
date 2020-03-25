---
title: Błąd krytyczny NMAKE U1059
ms.date: 08/27/2018
f1_keywords:
- U1059
helpviewer_keywords:
- U1059
ms.assetid: b21d9198-9c63-40d0-b589-80e17294ce24
ms.openlocfilehash: 33be3312e1f0aaa7f1e8aad64b44ea9aefd25346
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80182841"
---
# <a name="nmake-fatal-error-u1059"></a>Błąd krytyczny NMAKE U1059

> Błąd składniowy: Brak znaku "}" w elemencie Dependent

Ścieżka wyszukiwania dla elementu zależnego została niepoprawnie określona. W ścieżce lub nawias zamykający ( **}** ) został pominięty.

Składnia specyfikacji katalogu dla elementu zależnego to

> **zależne od** **{** *katalogi* }

gdzie *katalogi* określa jedną lub więcej ścieżek, każda z nich oddzielona średnikiem ( **;** ). Spacje nie są dozwolone.

Jeśli część lub cała ścieżka wyszukiwania jest zastępowana przez makro, upewnij się, że nie ma żadnych spacji w rozwinięciu makra.
