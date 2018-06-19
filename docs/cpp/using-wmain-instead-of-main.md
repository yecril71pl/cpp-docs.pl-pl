---
title: Korzystanie z wmain zamiast main | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- wmain
dev_langs:
- C++
helpviewer_keywords:
- main function, vs. wmain
- wmain function
ms.assetid: 7abb1257-b85c-413a-b913-d45b1582a71d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1f8f916fd6716678218b1b9b3d5d8b2e21a37c29
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32422206"
---
# <a name="using-wmain-instead-of-main"></a>Korzystanie z wmain zamiast main
## <a name="microsoft-specific"></a>Specyficzne dla firmy Microsoft  
 W modelu programowania Unicode, można określić wersji znaków dwubajtowych **głównego** funkcji. Użyj **wmain** zamiast **głównego** Aby napisać kod przenośny, który jest zgodna ze specyfikacją Unicode.  
  
 Deklarowanie parametrów formalnych do **wmain** formacie podobne do **głównego**. Następnie można przekazać argumenty znaków dwubajtowych i, opcjonalnie, wskaźnik znaków dwubajtowych środowiska do programu. `argv` i `envp` parametry **wmain** typu `wchar_t*`.  
  
 Jeśli używany przez program **głównego** funkcji środowiska znaków wielobajtowych jest tworzony przez system operacyjny w momencie uruchamiania programu. Zostanie utworzona kopia znaków dwubajtowych środowiska, tylko w razie potrzeby (na przykład przez wywołanie do [_wgetenv —](../c-runtime-library/reference/getenv-wgetenv.md) lub [_wputenv —](../c-runtime-library/reference/putenv-wputenv.md) funkcji). W pierwszym wywołaniu `_wputenv`, lub w pierwszym wywołaniu `_wgetenv` po środowisko MBCS już istnieje, odpowiednie środowisko ciąg znaków dwubajtowych tworzy, a następnie jest wskazywana przez `_wenviron` zmiennej globalnej, czyli znaków dwubajtowych Wersja `_environ` zmiennej globalnej. W tym momencie dwie kopie środowiska (MBCS i Unicode) istnieje jednocześnie i są obsługiwane przez system operacyjny cały czas życia program.  
  
 Podobnie jeśli jest używany przez program **wmain** funkcji środowisku MBCS (ASCII) jest tworzony w pierwszym wywołaniu `_putenv` lub `getenv`i jest wskazywana przez `_environ` zmiennej globalnej.  
  
 Aby uzyskać więcej informacji o środowisku MBCS, zobacz [zestawów znaków wielobajtowych i jednobajtowych](../c-runtime-library/single-byte-and-multibyte-character-sets.md) w *odwołanie do biblioteki czasu wykonywania.*  
  
**KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [main: uruchamianie programu](../cpp/main-program-startup.md)