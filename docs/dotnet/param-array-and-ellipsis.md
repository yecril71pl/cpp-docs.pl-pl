---
title: Tablica parametrów i wielokropek | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- function overloading, argument matching
ms.assetid: 492e3f6c-1c4c-4e0c-a358-72f2d39c30be
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 20d13f327abe3e864007c4941af2ce9fd03ea05d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="param-array-and-ellipsis"></a>Tablica parametrów i wielokropek
Pierwszeństwo w tablicy parametrów wywołania przeciążonej funkcji rozpoznawania został zmieniony z rozszerzeń zarządzanych dla języka C++ dla Visual C++.  
  
 Zarówno w przypadku rozszerzeń zarządzanych, jak i nowej składni nie jest jawną obsługiwane dla tablicy param C# i Visual Basic obsługuje. Zamiast tego co flagi zwykłej tablicy z atrybutem w następujący sposób:  
  
```  
void Trace1( String* format, [ParamArray]Object* args[] );  
void Trace2( String* format, Object* args[] );  
```  
  
 Gdy te zarówno wyglądu, `ParamArray` atrybutu znaczniki to dla języka C# lub innych języków CLR jako tablica biorąc zmienną liczbę elementów przy każdym wywołaniu. Zmiana zachowania w programach między rozszerzeń zarządzanych i nowej składni jest rozdzielczość przeciążonej funkcji w jednym wystąpieniu, z którym deklaruje wielokropek i drugi deklaruje `ParamArray` atrybutu, jak w poniższym przykładzie dostarczone przez Artur Laksberg.  
  
```  
int fx(...); // 1  
int fx( [ParamArray] Int32[] ); // 2  
```  
  
 W zarządzanych rozszerzeń wielokropka miało pierwszeństwo przez atrybut, który jest uzasadnione, ponieważ atrybut nie jest posiadanie aspekt języka. Jednak w nowej składni tablicy parametrów jest teraz obsługiwana bezpośrednio z poziomu języka i jego mają pierwszeństwo nad wielokropka ponieważ jest bardziej silnie typizowane. W związku z tym w zarządzanych rozszerzeń wywołania  
  
```  
fx( 1, 2 );  
```  
  
 jest rozpoznawana jako `fx(...)` znajduje się w nowej składni rozpoznawany `ParamArray` wystąpienia. Na off ryzyko, że Twoje zachowanie programu zależy od wywołania wystąpienia wielokropka porównaniu z `ParamArray`, należy zmodyfikować wywołania lub podpisu.  
  
## <a name="see-also"></a>Zobacz też  
 [Ogólne zmiany w języku (C++/CLI)](../dotnet/general-language-changes-cpp-cli.md)