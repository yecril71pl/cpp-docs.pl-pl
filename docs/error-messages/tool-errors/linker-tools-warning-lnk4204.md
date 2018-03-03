---
title: "Ostrzeżenie LNK4204 narzędzi konsolidatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK4204
dev_langs:
- C++
helpviewer_keywords:
- LNK4204
ms.assetid: 14adda20-0cbe-407b-90f6-9f81c93530e2
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0f9b2d9611192fe4afe01d178ac3af5fcc8ccc42
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-warning-lnk4204"></a>Ostrzeżenie LNK4204 narzędzi konsolidatora
"filename" nie ma informacji debugowania dla przywołującego modułu; Łączenie obiekt zostanie skonsolidowany bez informacji debugowania  
  
 Plik PDB ma błędny podpis. Konsolidator będą w dalszym ciągu połączyć obiekt bez informacji debugowania. Można ponownie skompilować przy użyciu pliku obiektu [/zi](../../build/reference/z7-zi-zi-debug-information-format.md) opcji.  
  
 LNK4204 może wystąpić, jeśli niektórych obiektów biblioteki odwołują się do pliku, który już nie istnieje. Może się to zdarzyć podczas odbudowywania rozwiązania, na przykład; Plik obiektu może być usunięte i nie odbudować z powodu błędu kompilacji. W takim przypadku albo kompilacji z **/z7**, lub **/Fd**, aby zaktualizować obiektów do odwoływania się do pojedynczego pliku dla biblioteki (który nie jest to domyślna nazwa pliku .pdb).  Aby uzyskać więcej informacji, zobacz [/Fd (nazwa pliku bazy danych programu)](../../build/reference/fd-program-database-file-name.md).  Upewnij się, że .pdb został zapisany z biblioteką za każdym razem, gdy jest aktualizowana w systemie kontroli źródła.