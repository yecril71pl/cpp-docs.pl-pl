---
title: Kompilatora (poziom 1) ostrzeżenie C4049 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4049
dev_langs:
- C++
helpviewer_keywords:
- C4049
ms.assetid: d11c1870-bcfc-4d71-8945-b87ec6ec3514
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1eea293ff64ed8fe2bf4bf0d38d897eb82223802
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4049"></a>Kompilator C4049 ostrzegawcze (poziom 1)
ograniczenie kompilatora: Kończenie emisji numeru wiersza  
  
 Plik zawiera więcej niż 16 777 215 (2<sup>24</sup>-1) źródło wierszy. Kompilator zatrzymuje numerowanie przy 16 777 215.  
  
 Dla kodu po wierszu 16 777 215:  
  
-   Obraz zostanie nie zawierają żadnych informacji debugowania dla numerów wierszy.  
  
-   Niektóre funkcje diagnostyczne może zostać zgłoszony z numerami nieprawidłowy wiersz.  
  
-   listy .asm (/ FAs) mogą mieć nieprawidłowe numery.