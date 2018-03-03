---
title: "Funkcje wewnętrzne i zestaw wbudowany | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 8affd4bb-279d-46f3-851f-8be0a9c5ed3f
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 80eb16eb7fde49c499227bb3d60000e2ac6e5143
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="intrinsics-and-inline-assembly"></a>Funkcje wewnętrzne i zestaw wbudowany
Jeden z warunków ograniczających dla [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] kompilatora ma nie obsługują asemblera wbudowanego. Oznacza to, że funkcje, które nie można zapisać w języka C lub C++ albo musi być zapisywane jako podprocedury lub funkcje wewnętrzne obsługiwane przez kompilator. Niektóre funkcje są wydajności poufnych, a inni nie. Funkcje zależne od wydajności powinny zostać wdrożone jako funkcje wewnętrzne.  
  
 Funkcje wewnętrzne, obsługiwane przez kompilator opisanym w [funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Konwencje kodowania x64](../build/x64-software-conventions.md)