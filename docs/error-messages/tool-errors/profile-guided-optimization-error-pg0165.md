---
title: PG0165 błąd optymalizacji sterowanych profilem | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: acad97411480112d06dadd454d1368dcfdf2c87f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="profile-guided-optimization-error-pg0165"></a>Błąd optymalizacji sterowanej profilem PG0165
Odczytywanie "Filename.pgd": "nie jest obsługiwana wersja pliku PGD (niezgodność wersji)".  
  
 Pliki PGD są specyficzne dla kompilatora określonego zestawu narzędzi. Ten błąd jest generowany, korzystając z różnych kompilatora niż to używane do *Filename*.pgd. Ten błąd wskazuje, że ten zestaw narzędzi kompilatora nie można użyć danych z *Filename*.pgd do optymalizacji bieżącego programu.  
  
 Aby rozwiązać ten problem, ponownie wygenerować *Filename*.pgd przy użyciu bieżącego zestawu narzędzi kompilatora.