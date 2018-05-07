---
title: Kompilatora (poziom 4) ostrzeżenie C4718 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4718
dev_langs:
- C++
helpviewer_keywords:
- C4718
ms.assetid: 29507f8a-b024-42c1-a3b8-f35d1f2641f3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a92ab7a32babd181f282c799568e3a9dea436c49
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-4-c4718"></a>Kompilator C4718 ostrzegawcze (poziom 4)
"wywołanie funkcji": wywołanie cykliczne nie ma żadnych efektów ubocznych, usuwanie  
  
 Funkcja zawiera wywołanie cykliczne, ale w przeciwnym razie nie ma skutków ubocznych. Wywołanie tej funkcji jest usuwany. Nie dotyczy poprawność program, ale jest zachowanie. Natomiast pozostawienie wywołanie może spowodować wyjątek czasu wykonywania przepełnienie stosu, wywołanie usunięcie tej możliwości.