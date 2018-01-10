---
title: "Błąd krytyczny C1061 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C1061
dev_langs: C++
helpviewer_keywords: C1061
ms.assetid: 9366c0bc-96e0-4967-aa7d-4ebf098de806
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 81963b0fffdf1b86b56b10c0776874b37ae9daa2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="fatal-error-c1061"></a>Błąd krytyczny C1061
limit kompilatora : blokuje zbyt głębokie zagnieżdżanie  
  
 Zagnieżdżanie bloków kodu przekracza limit 128 poziomów zagnieżdżenia. Jest to stały limit w kompilatorze dla C i C++, w zestawie narzędzi 32-bitowych i 64-bitowych. Liczba poziomów zagnieżdżenia może być zwiększana przez wszystko, co tworzy zakres lub blok. Na przykład, wszystkie przestrzenie nazw, stosowanie dyrektyw, rozszerzenia preprocesora, rozszerzenie szablonu, obsługa wyjątków, konstrukcje pętli i klauzule else-if mogą zwiększyć poziom zagnieżdżenia, jaki widzi kompilator.  
  
 Aby naprawić ten błąd, musisz wykonać refaktoryzację kodu. W każdym przypadku głęboko zagnieżdżony kod trudno zrozumieć i poprawić. Refaktoryzacja kodu, której celem jest zmniejszenie liczby poziomów zagnieżdżenia, może poprawić jakość kodu i uprościć zarządzanie nim. Podziel głęboko zagnieżdżony kod na funkcje, które są wywoływane z oryginalnego kontekstu. Ogranicz liczbę pętli lub połączonych klauzul else-if w bloku.