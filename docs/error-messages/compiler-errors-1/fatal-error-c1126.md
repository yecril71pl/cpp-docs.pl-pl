---
title: Błąd krytyczny C1126
ms.date: 11/04/2016
f1_keywords:
- C1126
helpviewer_keywords:
- C1126
ms.assetid: f22b26a6-8ad7-47cf-a237-196c8ea60aca
ms.openlocfilehash: a6c9d06cd087eb4462ae475cc1f6d64ba451887f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80203652"
---
# <a name="fatal-error-c1126"></a>Błąd krytyczny C1126

"Identyfikator": Alokacja automatyczna przekracza rozmiar

Miejsce przydzielone na zmienne lokalne funkcji (oraz ograniczoną ilość miejsca używanej przez kompilator, takie jak dodatkowe 20 bajtów dla funkcji do zamiany) przekracza limit.

Aby naprawić ten błąd, należy użyć `malloc` lub `new` do przydzielenia dużych ilości danych.
