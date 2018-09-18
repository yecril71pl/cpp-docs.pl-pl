---
title: Błąd krytyczny C1054 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1054
dev_langs:
- C++
helpviewer_keywords:
- C1054
ms.assetid: 9cfb7307-b22a-4418-b7c0-2621b0ab5b1b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 439019b1f510127ae54e77d445d59e86be09a49b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46101972"
---
# <a name="fatal-error-c1054"></a>Błąd krytyczny C1054

ograniczenie kompilatora: inicjatory są zagnieżdżone zbyt głęboko

Kod przekracza limit zagnieżdżania inicjatory (w zależności od kombinacji typów inicjowany poziomy 10 – 15).

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Aby rozwiązać problem, korzystając z poniższymi możliwymi rozwiązaniami

1. Uprość inicjowany, aby zmniejszyć zagnieżdżanie typów danych.

1. Po zadeklarowaniu, należy zainicjować zmienne w osobnych instrukcji.