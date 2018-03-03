---
title: Korzystanie z wmain | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- wmain function
ms.assetid: d0300812-adc4-40c6-bba3-b2da25468c80
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 47340642a8c18adfe5e371baca8daca7bd22f28d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="using-wmain"></a>wmain — korzystanie
**Dotyczące firmy Microsoft**  
  
 W modelu programowania Unicode, można określić wersji znaków dwubajtowych **głównego** funkcji. Użyj **wmain** zamiast **głównego** Aby napisać kod przenośny, zgodną Unicode model programowania.  
  
## <a name="syntax"></a>Składnia  
  
```  
wmain( int argc, wchar_t *argv[ ], wchar_t *envp[ ] )  
```  
  
## <a name="remarks"></a>Uwagi  
 Deklarowanie parametrów formalnych do **wmain** formacie podobne do **głównego**. Następnie można przekazać argumenty znaków dwubajtowych i, opcjonalnie, wskaźnik znaków dwubajtowych środowiska do programu. `argv` i `envp` parametry **wmain** typu `wchar_t*`. Na przykład:  
  
 Jeśli używany przez program **głównego** funkcji środowiska znaków wielobajtowych jest tworzony przez biblioteki wykonawczej w momencie uruchamiania programu. Zostanie utworzona kopia znaków dwubajtowych środowiska, tylko w razie potrzeby (na przykład przez wywołanie do `_wgetenv` lub `_wputenv` funkcji). W pierwszym wywołaniu `_wputenv`, lub w pierwszym wywołaniu `_wgetenv` po środowisko MBCS już istnieje, odpowiednie środowisko ciąg znaków dwubajtowych tworzy, a następnie jest wskazywana przez `_wenviron` zmiennej globalnej, czyli znaków dwubajtowych Wersja `_environ` zmiennej globalnej. W tym momencie dwie kopie środowiska (MBCS i Unicode) istnieje jednocześnie i są obsługiwane przez system operacyjny cały czas życia program.  
  
 Podobnie jeśli jest używany przez program **wmain** funkcji, jest tworzony w momencie uruchamiania programu środowiska znaków dwubajtowych i jest wskazywana przez `_wenviron` zmiennej globalnej. Środowisko MBCS (ASCII) jest tworzony w pierwszym wywołaniu `_putenv` lub `getenv`i jest wskazywana przez `_environ` zmiennej globalnej.  
  
 Aby uzyskać więcej informacji o środowisku MBCS, zobacz [internacjonalizacji](../c-runtime-library/internationalization.md) w *odwołanie do biblioteki czasu wykonywania.*  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcja main i wykonywanie programu](../c-language/main-function-and-program-execution.md)