---
title: Błąd krytyczny C1126
ms.date: 11/04/2016
f1_keywords:
- C1126
helpviewer_keywords:
- C1126
ms.assetid: f22b26a6-8ad7-47cf-a237-196c8ea60aca
ms.openlocfilehash: 3f4d152163d3b21ddf99644c34e63f35ca15e6e9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62230015"
---
# <a name="fatal-error-c1126"></a>Błąd krytyczny C1126

'Identyfikator': Automatyczna alokacja przekracza rozmiar

Ilość miejsca przydzielonego dla zmiennych lokalnych funkcji (plus ograniczona ilość miejsca używanego przez kompilator, takich jak dodatkowe 20 bajtów dla funkcji swappable) przekracza limit.

Aby rozwiązać ten problem, należy użyć `malloc` lub `new` do przydzielania dużej ilości danych.