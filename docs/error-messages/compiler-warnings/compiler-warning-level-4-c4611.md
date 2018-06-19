---
title: Kompilatora (poziom 4) ostrzeżenie C4611 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4611
dev_langs:
- C++
helpviewer_keywords:
- C4611
ms.assetid: bd90d0a6-75f9-4e97-968d-dda6773e9fd8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5946c10b5e0e0e7e08f1ee37c77120896937adb1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33293156"
---
# <a name="compiler-warning-level-4-c4611"></a>Kompilator C4611 ostrzegawcze (poziom 4)
Interakcja między "function" i zniszczeniem obiektu języka C++ nie jest przenośna  
  
 Na niektórych platformach, funkcje, które obejmują **catch** może nie obsługiwać semantyki obiektu C++ likwidacji, gdy znajdują się poza zakresem.  
  
 Aby uniknąć nieoczekiwanego zachowania, należy unikać **catch** w funkcje, które mają konstruktory i destruktory.  
  
 To ostrzeżenie zostanie wyświetlone tylko raz; zobacz [warning elementu pragma](../../preprocessor/warning.md).