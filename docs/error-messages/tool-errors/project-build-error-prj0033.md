---
title: Błąd PRJ0033 kompilacji projektu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0033
dev_langs:
- C++
helpviewer_keywords:
- PRJ0033
ms.assetid: 84d4a052-0586-4b78-9315-81c1e8386c1e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2722bc53fe267d3327f265578435cb672c58d3f4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33317063"
---
# <a name="project-build-error-prj0033"></a>Błąd PRJ0033 kompilacji projektu
Właściwość 'Dodatkowe zależności' dla niestandardowej kompilacji kroku dla pliku 'Plik' zawiera 'makra"co ewaluowane"macro_expansion".  
  
 Niestandardowego kroku kompilacji na plik zawiera błąd w jego dodatkowe zależności, prawdopodobnie z powodu problemu ocena makra. Ten błąd może również oznaczać czy ścieżka jest nieprawidłowo sformułowany, zawierające znaki lub kombinacji znaków, które są niedozwolone w ścieżce pliku.  
  
 Aby rozwiązać ten problem, Usuń makro lub usuń specyfikacji ścieżki. Obliczane ścieżka jest ścieżką bezwzględną od katalogu projektu.