---
title: "Statement (C) złożona | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- compound statements
- statements, compound
ms.assetid: 32d1bf86-cbbc-42a9-ba3a-1be1c6c7754c
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 369ff1b3097e79fa0da50a82647bbf6ac62464e2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compound-statement-c"></a>Instrukcja złożona (C)
Instrukcja złożona (również o nazwie "blok") zwykle pojawia się jako treść inną instrukcję, takich jak **Jeśli** instrukcji. [Deklaracje i typy](../c-language/declarations-and-types.md) opisuje formularza i znaczenie deklaracje, które mogą być wyświetlane w nagłówek złożonej instrukcji.  
  
## <a name="syntax"></a>Składnia  
 *instrukcji złożonej*:  
 **{***lista deklaracji* opt*listy instrukcji*opt**}**   
  
 *Lista deklaracji*:  
 *Deklaracja*  
  
 *Lista deklaracji deklaracji*  
  
 *Lista instrukcji*:  
 s*zestawienia*  
  
 *Instrukcja listy — instrukcja*  
  
 W przypadku deklaracje muszą pochodzić przed wszystkimi instrukcjami. Zakres każdy identyfikator zadeklarowane na początku złożonej instrukcji rozciąga się od punktu deklaracji na końcu bloku. Jest widoczne w bloku, chyba że o takim samym identyfikatorze istnieje w bloku wewnętrznym.  
  
 Identyfikatory w złożonej instrukcji są domniemania **automatycznie** , chyba że jawnie zadeklarowana w przeciwnym razie z **zarejestrować**, **statycznych**, lub `extern`, z wyjątkiem funkcji, który może być tylko `extern`. Można pozostawić wyłączone `extern` nadal będzie specyfikator w deklaracji funkcji i funkcji `extern`.  
  
 Magazyn nie jest przydzielony i inicjowanie nie jest dozwolone, jeśli zmienna lub funkcja jest zadeklarowana w instrukcji złożonej przy użyciu klasy magazynu `extern`. Deklaracja odnosi się do zmiennej zewnętrznych lub funkcja zdefiniowana w innym miejscu.  
  
 Zmienne zadeklarowane w bloku z **automatycznie** lub **zarejestrować** — słowo kluczowe są ponownie rozdzielone i, jeśli to konieczne, zainicjować zawsze jest wprowadzana złożonej instrukcji. Te zmienne nie są zdefiniowane po złożonej instrukcji zostanie zakończone. Zmienna zadeklarowana wewnątrz bloku ma **statycznych** atrybutu, zmienna jest zainicjowana podczas wykonywania programu rozpoczyna się i zachowując jego wartość w programie. Zobacz [klasy magazynu](../c-language/c-storage-classes.md) informacji o **statycznych**.  
  
 W tym przykładzie przedstawiono złożonej instrukcji:  
  
```  
if ( i > 0 )   
{  
    line[i] = x;  
    x++;  
    i--;  
}  
```  
  
 W tym przykładzie Jeśli `i` jest większa niż 0, wszystkie instrukcje wewnątrz instrukcji złożone są wykonywane w kolejności.  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje](../c-language/statements-c.md)