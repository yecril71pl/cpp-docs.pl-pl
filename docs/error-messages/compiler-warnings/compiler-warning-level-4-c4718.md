---
title: "Kompilatora (poziom 4) ostrzeżenie C4718 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4718
dev_langs: C++
helpviewer_keywords: C4718
ms.assetid: 29507f8a-b024-42c1-a3b8-f35d1f2641f3
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 837e0e69d2a2f0694dc9c99e8c3425bbd12a94e2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-4-c4718"></a>Kompilator C4718 ostrzegawcze (poziom 4)
"wywołanie funkcji": wywołanie cykliczne nie ma żadnych efektów ubocznych, usuwanie  
  
 Funkcja zawiera wywołanie cykliczne, ale w przeciwnym razie nie ma skutków ubocznych. Wywołanie tej funkcji jest usuwany. Nie dotyczy poprawność program, ale jest zachowanie. Natomiast pozostawienie wywołanie może spowodować wyjątek czasu wykonywania przepełnienie stosu, wywołanie usunięcie tej możliwości.