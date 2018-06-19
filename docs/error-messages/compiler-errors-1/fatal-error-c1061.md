---
title: Błąd krytyczny C1061 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1061
dev_langs:
- C++
helpviewer_keywords:
- C1061
ms.assetid: 9366c0bc-96e0-4967-aa7d-4ebf098de806
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fde2d3a076b4cf78a8104fd19719bec205828c68
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33225705"
---
# <a name="fatal-error-c1061"></a>Błąd krytyczny C1061
limit kompilatora : blokuje zbyt głębokie zagnieżdżanie  
  
 Zagnieżdżanie bloków kodu przekracza limit 128 poziomów zagnieżdżenia. Jest to stały limit w kompilatorze dla C i C++, w zestawie narzędzi 32-bitowych i 64-bitowych. Liczba poziomów zagnieżdżenia może być zwiększana przez wszystko, co tworzy zakres lub blok. Na przykład, wszystkie przestrzenie nazw, stosowanie dyrektyw, rozszerzenia preprocesora, rozszerzenie szablonu, obsługa wyjątków, konstrukcje pętli i klauzule else-if mogą zwiększyć poziom zagnieżdżenia, jaki widzi kompilator.  
  
 Aby naprawić ten błąd, musisz wykonać refaktoryzację kodu. W każdym przypadku głęboko zagnieżdżony kod trudno zrozumieć i poprawić. Refaktoryzacja kodu, której celem jest zmniejszenie liczby poziomów zagnieżdżenia, może poprawić jakość kodu i uprościć zarządzanie nim. Podziel głęboko zagnieżdżony kod na funkcje, które są wywoływane z oryginalnego kontekstu. Ogranicz liczbę pętli lub połączonych klauzul else-if w bloku.