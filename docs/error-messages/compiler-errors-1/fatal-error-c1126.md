---
title: Błąd krytyczny C1126
ms.date: 11/04/2016
f1_keywords:
- C1126
helpviewer_keywords:
- C1126
ms.assetid: f22b26a6-8ad7-47cf-a237-196c8ea60aca
ms.openlocfilehash: 110fbfe984ee7714e0c8ee2e2cb4deec4f43905a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87207930"
---
# <a name="fatal-error-c1126"></a>Błąd krytyczny C1126

"Identyfikator": Alokacja automatyczna przekracza rozmiar

Miejsce przydzielone na zmienne lokalne funkcji (oraz ograniczoną ilość miejsca używanej przez kompilator, takie jak dodatkowe 20 bajtów dla funkcji do zamiany) przekracza limit.

Aby naprawić ten błąd, użyj `malloc` lub, **`new`** Aby przydzielić duże ilości danych.
