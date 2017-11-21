---
title: Funkcja Call (C) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- function calls, C functions
- functions [C], calling
- function calls
ms.assetid: 35c66719-3f15-4d3b-97da-4e19dc97b308
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0faf339877b075a1337c73ec5ca3c41a869ceec2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="function-call-c"></a>Wywołanie funkcji (C)
"Wywołanie funkcji" to wyrażenie, która zawiera nazwę wywoływanej funkcji lub wartość wskaźnika funkcji i, opcjonalnie, argumenty przekazywany do funkcji.  
  
## <a name="syntax"></a>Składnia  
 *Operatory przyrostka wyrażenie*:  
 *wyrażenie przyrostek***(***lista wyrażeń argument* opt**)**   
  
 *Lista wyrażeń argument*:  
 *wyrażenia przypisania*  
  
 *Lista wyrażeń argument***,***wyrażenia przypisania*   
  
 *Wyrażenie przyrostek* musi być adresem funkcji (na przykład identyfikator funkcji lub wartość wskaźnika funkcji), i *lista wyrażeń argument* znajduje się lista wyrażeń (oddzielone przecinkami) których wartości ("argumentów") są przekazywane do funkcji. *Lista wyrażeń argument* argument może być pusta.  
  
 Wyrażenie wywołania funkcji ma wartość i typ wartości zwracanej przez funkcję. Funkcja nie może zwracać obiektu typu array. Jeśli funkcja zwracany typ jest `void` (oznacza to, że funkcja została zadeklarowana nigdy nie, aby zwrócić wartość), ma także wyrażenie wywołania funkcji `void` typu. (Zobacz [wywołania funkcji](../c-language/function-calls.md) Aby uzyskać więcej informacji.)  
  
## <a name="see-also"></a>Zobacz też  
 [Operator wywołania funkcji:)](../cpp/function-call-operator-parens.md)