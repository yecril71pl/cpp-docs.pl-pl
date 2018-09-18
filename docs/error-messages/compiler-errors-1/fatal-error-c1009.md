---
title: Błąd krytyczny C1009 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1009
dev_langs:
- C++
helpviewer_keywords:
- C1009
ms.assetid: dcc8383c-3362-4c47-9c26-25d2451ebd53
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b1fbd8994be6fd86a764db400d8761a5d697079b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46037336"
---
# <a name="fatal-error-c1009"></a>Błąd krytyczny C1009

ograniczenie kompilatora: makra są zagnieżdżone zbyt głęboko

Kompilator próbował rozwinąć makra zbyt wiele, w tym samym czasie. Kompilator ma limit wynoszący 256 poziomów zagnieżdżonych makra. Podziel zagnieżdżonych makra na łatwiejsze makra.