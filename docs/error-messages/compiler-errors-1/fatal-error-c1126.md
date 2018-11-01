---
title: Błąd krytyczny C1126
ms.date: 11/04/2016
f1_keywords:
- C1126
helpviewer_keywords:
- C1126
ms.assetid: f22b26a6-8ad7-47cf-a237-196c8ea60aca
ms.openlocfilehash: 3f4d152163d3b21ddf99644c34e63f35ca15e6e9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50457784"
---
# <a name="fatal-error-c1126"></a>Błąd krytyczny C1126

'Identyfikator': Automatyczna alokacja przekracza rozmiar

Ilość miejsca przydzielonego dla zmiennych lokalnych funkcji (plus ograniczona ilość miejsca używanego przez kompilator, takich jak dodatkowe 20 bajtów dla funkcji swappable) przekracza limit.

Aby rozwiązać ten problem, należy użyć `malloc` lub `new` do przydzielania dużej ilości danych.