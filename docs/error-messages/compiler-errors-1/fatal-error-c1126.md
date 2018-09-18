---
title: Błąd krytyczny C1126 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1126
dev_langs:
- C++
helpviewer_keywords:
- C1126
ms.assetid: f22b26a6-8ad7-47cf-a237-196c8ea60aca
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f014aafc60a36bfbb4edad50e7e3ceede6e3c8b2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46062478"
---
# <a name="fatal-error-c1126"></a>Błąd krytyczny C1126

'Identyfikator': Automatyczna alokacja przekracza rozmiar

Ilość miejsca przydzielonego dla zmiennych lokalnych funkcji (plus ograniczona ilość miejsca używanego przez kompilator, takich jak dodatkowe 20 bajtów dla funkcji swappable) przekracza limit.

Aby rozwiązać ten problem, należy użyć `malloc` lub `new` do przydzielania dużej ilości danych.