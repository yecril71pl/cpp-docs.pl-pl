---
title: "Składnia wiersza polecenia kompilatora | Dokumentacja firmy Microsoft"
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
helpviewer_keywords:
- syntax, CL compiler command line
- cl.exe compiler, command-line syntax
ms.assetid: acba2c1c-0803-4a3a-af25-63e849b930a2
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7fb89aca1990d44d7ef62ea76788b38e8ffa1d6d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-command-line-syntax"></a>Składnia wiersza polecenia kompilatora
W wierszu polecenia CL używa następującej składni:  
  
```  
CL [option...] file... [option | file]... [lib...] [@command-file] [/link link-opt...]  
```  
  
 W poniższej tabeli opisano dane wejściowe polecenia CL.  
  
|Wpis|Znaczenie|  
|-----------|-------------|  
|*Opcja*|Co najmniej jeden [opcji CL](../../build/reference/compiler-options.md). Należy pamiętać, że wszystkie opcje są stosowane do wszystkich plików określonego źródła. Opcje są określane przez ukośnika (/) i myślnik (-). Jeśli opcja przyjmuje argument, a opcja opis dokumenty czy spacji między opcją i argumenty. Opcja nazwy (z wyjątkiem opcji/Help) jest uwzględniana wielkość liter. Zobacz [kolejność opcji CL](../../build/reference/order-of-cl-options.md) Aby uzyskać więcej informacji.|  
|`file`|Nazwa jednego lub więcej plików źródłowych, pliki obj lub biblioteki. CL kompiluje pliki źródłowe i przekazuje nazwy plików .obj i bibliotek konsolidatora. Zobacz [Składnia nazwy pliku CL](../../build/reference/cl-filename-syntax.md) Aby uzyskać więcej informacji.|  
|*lib*|Jeden lub więcej nazw bibliotek. CL przekazuje te nazwy do konsolidatora.|  
|*Plik poleceń*|Plik, który zawiera wiele opcji i nazwy plików. Zobacz [pliki poleceń CL](../../build/reference/cl-command-files.md) Aby uzyskać więcej informacji.|  
|*Link-opt*|Co najmniej jeden [opcje konsolidatora](../../build/reference/linker-options.md). CL przekazuje te opcje do konsolidatora.|  
  
 Można określić dowolną liczbę opcji, nazwy plików i nazw bibliotek, tak długo, jak liczba znaków w wierszu polecenia nie przekracza 1024, limit definiowane przez system operacyjny.  
  
 Aby uzyskać informacje o wartości zwracanej cl.exe, zobacz [zwrócić wartość cl.exe](../../build/reference/return-value-of-cl-exe.md) .  
  
> [!NOTE]
>  Jednocześnie w przyszłych wersjach systemu Windows nie jest gwarantowana wiersza polecenia wejściowych limit 1024 znaków.  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)   
 [Opcje kompilatora](../../build/reference/compiler-options.md)