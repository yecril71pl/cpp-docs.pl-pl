---
title: "Funkcje wewnętrzne i zestaw wbudowany | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 8affd4bb-279d-46f3-851f-8be0a9c5ed3f
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: c60932b719b25365c7d8f65a4649ef782a4f9888
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="intrinsics-and-inline-assembly"></a>Funkcje wewnętrzne i zestaw wbudowany
Jeden z warunków ograniczających dla [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] kompilatora ma nie obsługują asemblera wbudowanego. Oznacza to, że funkcje, które nie można zapisać w języka C lub C++ albo musi być zapisywane jako podprocedury lub funkcje wewnętrzne obsługiwane przez kompilator. Niektóre funkcje są wydajności poufnych, a inni nie. Funkcje zależne od wydajności powinny zostać wdrożone jako funkcje wewnętrzne.  
  
 Funkcje wewnętrzne, obsługiwane przez kompilator opisanym w [funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md).  
  
## <a name="see-also"></a>Zobacz też  
 [x64 konwencje kodowania](../build/x64-software-conventions.md)