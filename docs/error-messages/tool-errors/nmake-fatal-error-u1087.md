---
title: Błąd krytyczny NMAKE U1087
ms.date: 11/04/2016
f1_keywords:
- U1087
helpviewer_keywords:
- U1087
ms.assetid: 5236ab54-e117-484d-99c3-852b061fd3d0
ms.openlocfilehash: 47015443114404de2e5f9edfdb1100c324d5e18b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62298454"
---
# <a name="nmake-fatal-error-u1087"></a>Błąd krytyczny NMAKE U1087

nie może mieć: i:: elementów zależnych dla tego samego obiektu docelowego.

Element docelowy nie można określić w obu pojedynczego dwukropek (**:**) i podwójnego dwukropka (`::`) zależności.

Aby określić obiekt docelowy w blokach opisów, użyj `::` w każdym wierszu zależności.