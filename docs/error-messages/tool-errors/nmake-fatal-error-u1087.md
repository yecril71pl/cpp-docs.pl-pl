---
title: Błąd krytyczny NMAKE U1087
ms.date: 11/04/2016
f1_keywords:
- U1087
helpviewer_keywords:
- U1087
ms.assetid: 5236ab54-e117-484d-99c3-852b061fd3d0
ms.openlocfilehash: 47015443114404de2e5f9edfdb1100c324d5e18b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50527975"
---
# <a name="nmake-fatal-error-u1087"></a>Błąd krytyczny NMAKE U1087

nie może mieć: i:: elementów zależnych dla tego samego obiektu docelowego.

Element docelowy nie można określić w obu pojedynczego dwukropek (**:**) i podwójnego dwukropka (`::`) zależności.

Aby określić obiekt docelowy w blokach opisów, użyj `::` w każdym wierszu zależności.