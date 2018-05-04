---
title: Funkcje wewnętrzne i zestaw wbudowany | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 8affd4bb-279d-46f3-851f-8be0a9c5ed3f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5b8651bea0b1ee9f54ec0af704d92feef0722368
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="intrinsics-and-inline-assembly"></a>Funkcje wewnętrzne i zestaw wbudowany
Jeden z warunków ograniczających dla [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] kompilatora ma nie obsługują asemblera wbudowanego. Oznacza to, że funkcje, które nie można zapisać w języka C lub C++ albo musi być zapisywane jako podprocedury lub funkcje wewnętrzne obsługiwane przez kompilator. Niektóre funkcje są wydajności poufnych, a inni nie. Funkcje zależne od wydajności powinny zostać wdrożone jako funkcje wewnętrzne.  
  
 Funkcje wewnętrzne, obsługiwane przez kompilator opisanym w [funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Konwencje kodowania x64](../build/x64-software-conventions.md)