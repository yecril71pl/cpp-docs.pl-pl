---
title: "Kompilatora (poziom 1) ostrzeżenie C4049 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4049
dev_langs:
- C++
helpviewer_keywords:
- C4049
ms.assetid: d11c1870-bcfc-4d71-8945-b87ec6ec3514
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 15d76be8cdf9855435094d02be5bc28fe27fe89a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4049"></a>Kompilator C4049 ostrzegawcze (poziom 1)
ograniczenie kompilatora: Kończenie emisji numeru wiersza  
  
 Plik zawiera więcej niż 16 777 215 (2<sup>24</sup>-1) źródło wierszy. Kompilator zatrzymuje numerowanie przy 16 777 215.  
  
 Dla kodu po wierszu 16 777 215:  
  
-   Obraz zostanie nie zawierają żadnych informacji debugowania dla numerów wierszy.  
  
-   Niektóre funkcje diagnostyczne może zostać zgłoszony z numerami nieprawidłowy wiersz.  
  
-   listy .asm (/ FAs) mogą mieć nieprawidłowe numery.