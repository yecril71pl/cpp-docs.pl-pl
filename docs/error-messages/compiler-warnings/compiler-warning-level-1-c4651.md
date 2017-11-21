---
title: "Kompilatora (poziom 1) ostrzeżenie C4651 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4651
dev_langs: C++
helpviewer_keywords: C4651
ms.assetid: f1ea82aa-4dc1-4972-b55a-57fdb962f0dd
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: f1faffc6ba7b9df4fecefa3bef47f0418fdc8641
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4651"></a>Kompilator C4651 ostrzegawcze (poziom 1)
"definition" określony dla prekompilowanego nagłówka, ale nie dla bieżącej kompilacji  
  
 Definicja została określona podczas prekompilowany nagłówek został wygenerowany, ale nie znajduje się w tej kompilacji.  
  
 Definicja będzie obowiązywać wewnątrz prekompilowanego nagłówka, ale nie znajduje się w dalszej części kodu.  
  
 Jeśli został skompilowany /DSYMBOL prekompilowanego nagłówka, kompilator generuje to ostrzeżenie kompilacji /Yu powodował /DSYMBOL.  Dodawanie do wiersza polecenia /Yu /DSYMBOL rozpoznaje to ostrzeżenie.