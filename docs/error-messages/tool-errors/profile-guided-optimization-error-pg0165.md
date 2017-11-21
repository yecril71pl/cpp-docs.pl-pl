---
title: "PG0165 błąd optymalizacji sterowanych profilem | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: PG0165
dev_langs: C++
helpviewer_keywords: PG0165
ms.assetid: e98122e7-ddee-4a2c-96b2-d232e4c65f3e
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: dbc85ad329a990ecdd7bc3a05f28d16a0c58c8e8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="profile-guided-optimization-error-pg0165"></a>Błąd optymalizacji sterowanej profilem PG0165
Odczytywanie "Filename.pgd": "nie jest obsługiwana wersja pliku PGD (niezgodność wersji)".  
  
 Pliki PGD są specyficzne dla kompilatora określonego zestawu narzędzi. Ten błąd jest generowany, korzystając z różnych kompilatora niż to używane do *Filename*.pgd. Ten błąd wskazuje, że ten zestaw narzędzi kompilatora nie można użyć danych z *Filename*.pgd do optymalizacji bieżącego programu.  
  
 Aby rozwiązać ten problem, ponownie wygenerować *Filename*.pgd przy użyciu bieżącego zestawu narzędzi kompilatora.