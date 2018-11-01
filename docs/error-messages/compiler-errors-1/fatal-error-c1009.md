---
title: Błąd krytyczny C1009
ms.date: 11/04/2016
f1_keywords:
- C1009
helpviewer_keywords:
- C1009
ms.assetid: dcc8383c-3362-4c47-9c26-25d2451ebd53
ms.openlocfilehash: c4654d37f5ce184f6fa5b8888e6ca0184267be07
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50542665"
---
# <a name="fatal-error-c1009"></a>Błąd krytyczny C1009

ograniczenie kompilatora: makra są zagnieżdżone zbyt głęboko

Kompilator próbował rozwinąć makra zbyt wiele, w tym samym czasie. Kompilator ma limit wynoszący 256 poziomów zagnieżdżonych makra. Podziel zagnieżdżonych makra na łatwiejsze makra.