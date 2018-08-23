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
ms.openlocfilehash: ff2b99eedcdd81a96dc3091046a4f62ffe002509
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/14/2018
ms.locfileid: "42465136"
---
# <a name="intrinsics-and-inline-assembly"></a>Funkcje wewnętrzne i zestaw wbudowany
Jednym z ograniczeń x64 kompilatora ma nie obsługują asemblera wbudowanego. Oznacza to, że funkcji nie można zapisać w C lub C++, albo musi być zapisywane jako procedury lub funkcji wewnętrznych obsługiwanych przez kompilator. Niektóre funkcje są wrażliwe na wydajność, a inne nie. Funkcje wrażliwego na wydajność, powinny zostać wdrożone jako funkcje wewnętrzne.  
  
 Funkcje wewnętrzne, obsługiwane przez kompilator są opisane w [funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Konwencje kodowania x64](../build/x64-software-conventions.md)