---
title: Błąd krytyczny NMAKE U1087 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1087
dev_langs:
- C++
helpviewer_keywords:
- U1087
ms.assetid: 5236ab54-e117-484d-99c3-852b061fd3d0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2f0e094c720222990ee90af7de900d8cf6ba4051
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46036803"
---
# <a name="nmake-fatal-error-u1087"></a>Błąd krytyczny NMAKE U1087

nie może mieć: i:: elementów zależnych dla tego samego obiektu docelowego.

Element docelowy nie można określić w obu pojedynczego dwukropek (**:**) i podwójnego dwukropka (`::`) zależności.

Aby określić obiekt docelowy w blokach opisów, użyj `::` w każdym wierszu zależności.