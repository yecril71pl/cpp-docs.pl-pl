---
title: Przydzielanie pamięci zerowej | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- memory allocation, zero memory
- zero memory
ms.assetid: 768f2ab9-83a1-4887-8eb5-c094c18489a8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0de013e9ddd3fb983436bf6ee0db290458936eb5
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32380641"
---
# <a name="allocating-zero-memory"></a>Przydzielanie pamięci zerowej
**ANSI 4.10.3** zachowanie `calloc`, `malloc`, lub `realloc` działać, jeśli żądany rozmiar wynosi zero  
  
 `calloc`, `malloc`, I `realloc` funkcje są akceptowane wartości zerowe jako argument. Nie rzeczywiste jest rezerwowana pamięć, ale prawidłowego wskaźnika jest zwracany i blok pamięci można zmodyfikować później przy realloc.  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje bibliotek](../c-language/library-functions.md)