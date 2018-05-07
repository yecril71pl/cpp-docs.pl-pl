---
title: Ostrzeżenie LNK4102 narzędzi konsolidatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4102
dev_langs:
- C++
helpviewer_keywords:
- LNK4102
ms.assetid: bfd1b17e-05c7-4bc2-80d6-2888b1a425b2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 16d13dcbc6d15efd7cf3a7ea0a310de4ab7b0c93
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-warning-lnk4102"></a>Ostrzeżenie LNK4102 narzędzi konsolidatora
Eksport destruktora "name"; Usuwanie Obraz może nie działać poprawnie  
  
 Program próbował wyeksportować usuwania destruktora. Wynikowy delete mogą wystąpić granicy DLL tak, aby zwolnić pamięć, która nie jest właścicielem procesu. Upewnij się, że dany symbol nie jest wymieniony w pliku .def i że symbol nie jest wymieniony jako argument **/IMPORT** lub **/EXPORT** opcji wiersza polecenia konsolidatora.  
  
 Odbudowywania biblioteki wykonawczej języka C, możesz zignorować ten komunikat.