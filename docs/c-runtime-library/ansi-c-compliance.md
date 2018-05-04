---
title: Zgodność ANSI-C | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- Ansi
dev_langs:
- C++
helpviewer_keywords:
- underscores, leading
- compatibility [C++], ANSI C
- compliance with ANSI C
- conventions [C++], Microsoft extensions
- underscores
- naming conventions [C++], Microsoft library
- ANSI [C++], C standard
- Microsoft extensions naming conventions
ms.assetid: 6be271bf-eecf-491a-a928-0ee2dd60e3b9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 452c6803ea05f051727a1417aee49c3a56759141
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ansi-c-compliance"></a>Zgodność ANSI-C
Konwencja nazewnictwa dla wszystkich identyfikatorów specyficzne dla firmy Microsoft w systemie czasu wykonywania (na przykład funkcji, makra, stałe, zmienne i definicje typów) jest standardem ANSI. W tej dokumentacji dowolnej funkcji środowiska wykonawczego, który jest zgodny ze standardami ANSI/ISO C jest odnotowany jako zgodne ANSI. Aplikacje zgodne z ANSI należy używać tylko tych funkcji zgodne ANSI.  
  
 Nazwy funkcji specyficzne dla firmy Microsoft i zmienne globalne zaczynają się od jednego znaku podkreślenia. Te nazwy można zastąpić tylko lokalnie w zakresie kodu. Na przykład po dołączeniu pliki nagłówków środowiska wykonawczego Microsoft, możesz nadal lokalnie przesłonić funkcji specyficzne dla firmy Microsoft o nazwie `_open` przez deklarowanie zmiennej lokalnej o tej samej nazwie. Nie można jednak użyć tę nazwę do własnych funkcji globalnej lub zmiennej globalnej.  
  
 Nazwy makra specyficzne dla firmy Microsoft i stałe manifestu rozpocząć z dwóch znaków podkreślenia lub pojedynczy podkreślenia wiodące poprzedzającą wielką literę. Zakres takie identyfikatory jest bezwzględny. Na przykład nie można użyć identyfikatora specyficzne dla firmy Microsoft **_UPPER** z tego powodu.  
  
## <a name="see-also"></a>Zobacz też  
 [Zgodność](../c-runtime-library/compatibility.md)