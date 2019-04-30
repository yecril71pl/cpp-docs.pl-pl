---
title: Błąd krytyczny C1054
ms.date: 11/04/2016
f1_keywords:
- C1054
helpviewer_keywords:
- C1054
ms.assetid: 9cfb7307-b22a-4418-b7c0-2621b0ab5b1b
ms.openlocfilehash: 0bfd0c03378b1a9c616a014ac96153b3ab04af9d
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/24/2019
ms.locfileid: "64344796"
---
# <a name="fatal-error-c1054"></a>Błąd krytyczny C1054

ograniczenie kompilatora: inicjatory są zagnieżdżone zbyt głęboko

Kod przekracza limit zagnieżdżania inicjatory (w zależności od kombinacji typów inicjowany poziomy 10 – 15).

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Aby rozwiązać problem, korzystając z poniższymi możliwymi rozwiązaniami

1. Uprość inicjowany, aby zmniejszyć zagnieżdżanie typów danych.

1. Po zadeklarowaniu, należy zainicjować zmienne w osobnych instrukcji.