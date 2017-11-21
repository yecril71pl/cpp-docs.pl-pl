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
ms.openlocfilehash: 57766a4ff0b58fdc599a7124e217892e4b28539d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="fatal-error-c1061"></a>Błąd krytyczny C1061
limit kompilatora : blokuje zbyt głębokie zagnieżdżanie  
  
 Zagnieżdżanie bloków kodu przekracza limit 128 poziomów zagnieżdżenia. Jest to stały limit w kompilatorze dla C i C++, w zestawie narzędzi 32-bitowych i 64-bitowych. Liczba poziomów zagnieżdżenia może być zwiększana przez wszystko, co tworzy zakres lub blok. Na przykład, wszystkie przestrzenie nazw, stosowanie dyrektyw, rozszerzenia preprocesora, rozszerzenie szablonu, obsługa wyjątków, konstrukcje pętli i klauzule else-if mogą zwiększyć poziom zagnieżdżenia, jaki widzi kompilator.  
  
 Aby naprawić ten błąd, musisz wykonać refaktoryzację kodu. W każdym przypadku głęboko zagnieżdżony kod trudno zrozumieć i poprawić. Refaktoryzacja kodu, której celem jest zmniejszenie liczby poziomów zagnieżdżenia, może poprawić jakość kodu i uprościć zarządzanie nim. Podziel głęboko zagnieżdżony kod na funkcje, które są wywoływane z oryginalnego kontekstu. Ogranicz liczbę pętli lub połączonych klauzul else-if w bloku.