---
title: Ostrzeżenie LNK4204 narzędzi konsolidatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4204
dev_langs:
- C++
helpviewer_keywords:
- LNK4204
ms.assetid: 14adda20-0cbe-407b-90f6-9f81c93530e2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f000fa42357a299c943eda0cd5f8697aee138f4a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-warning-lnk4204"></a>Ostrzeżenie LNK4204 narzędzi konsolidatora
"filename" nie ma informacji debugowania dla przywołującego modułu; Łączenie obiekt zostanie skonsolidowany bez informacji debugowania  
  
 Plik PDB ma błędny podpis. Konsolidator będą w dalszym ciągu połączyć obiekt bez informacji debugowania. Można ponownie skompilować przy użyciu pliku obiektu [/zi](../../build/reference/z7-zi-zi-debug-information-format.md) opcji.  
  
 LNK4204 może wystąpić, jeśli niektórych obiektów biblioteki odwołują się do pliku, który już nie istnieje. Może się to zdarzyć podczas odbudowywania rozwiązania, na przykład; Plik obiektu może być usunięte i nie odbudować z powodu błędu kompilacji. W takim przypadku albo kompilacji z **/z7**, lub **/Fd**, aby zaktualizować obiektów do odwoływania się do pojedynczego pliku dla biblioteki (który nie jest to domyślna nazwa pliku .pdb).  Aby uzyskać więcej informacji, zobacz [/Fd (nazwa pliku bazy danych programu)](../../build/reference/fd-program-database-file-name.md).  Upewnij się, że .pdb został zapisany z biblioteką za każdym razem, gdy jest aktualizowana w systemie kontroli źródła.