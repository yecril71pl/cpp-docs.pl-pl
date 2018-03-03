---
title: "Ostrzeżenie LNK4102 narzędzi konsolidatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK4102
dev_langs:
- C++
helpviewer_keywords:
- LNK4102
ms.assetid: bfd1b17e-05c7-4bc2-80d6-2888b1a425b2
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 80efad60da9f6742110811a5cf4c12f07c7def67
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-warning-lnk4102"></a>Ostrzeżenie LNK4102 narzędzi konsolidatora
Eksport destruktora "name"; Usuwanie Obraz może nie działać poprawnie  
  
 Program próbował wyeksportować usuwania destruktora. Wynikowy delete mogą wystąpić granicy DLL tak, aby zwolnić pamięć, która nie jest właścicielem procesu. Upewnij się, że dany symbol nie jest wymieniony w pliku .def i że symbol nie jest wymieniony jako argument **/IMPORT** lub **/EXPORT** opcji wiersza polecenia konsolidatora.  
  
 Odbudowywania biblioteki wykonawczej języka C, możesz zignorować ten komunikat.