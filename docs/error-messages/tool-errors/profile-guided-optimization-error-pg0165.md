---
title: Błąd optymalizacji PG0165 sterowane profilem | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PG0165
dev_langs:
- C++
helpviewer_keywords:
- PG0165
ms.assetid: e98122e7-ddee-4a2c-96b2-d232e4c65f3e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 332751a123bf7d6414c40b79870b5edf27a3d8a7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46084214"
---
# <a name="profile-guided-optimization-error-pg0165"></a>Błąd optymalizacji sterowanej profilem PG0165

Odczytywanie "Filename.pgd": "nie jest obsługiwana wersja pliku PGD (niezgodność wersji)".

Pliki PGD są specyficzne dla kompilatora określonego zestawu narzędzi. Ten błąd jest generowany, gdy używasz innego kompilatora niż ten używany do *Filename*.pgd. Ten błąd wskazuje, że ten zestaw narzędzi kompilatora nie mogą używać danych z *Filename*.pgd do optymalizacji bieżącego programu.

Aby rozwiązać ten problem, należy ponownie wygenerować *Filename*.pgd przy użyciu bieżącego zestawu narzędzi kompilatora.