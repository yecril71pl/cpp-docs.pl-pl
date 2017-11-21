---
title: "2.6.5 dyrektywa opróżniania | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: a2ec5f74-9c37-424a-8376-47ab4a5829a2
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a1911efe811545c13e62ab9f917ddfc284af35b0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="265-flush-directive"></a>2.6.5 Dyrektywa opróżniania
**Opróżnić** dyrektywy, czy jawne lub domniemanych, określa jaką implementacja jest wymagana, aby zapewnić spójne wyświetlanie niektórych obiektów (wymienionymi poniżej), w wszystkie wątki w zespole punktu sekwencji "między wątkami" pamięci. To oznacza, że poprzednie ocen wyrażeń, które odwołują się do tych obiektów są spełnione, a kolejne oceny nie zostały jeszcze uruchomione. Na przykład kompilatory należy przywrócić wartości obiektów z rejestrów pamięci i sprzętu może być konieczne opróżnienia buforów zapisu w pamięci i załaduj ponownie wartości obiektów w pamięci.  
  
 Składnia **opróżnić** dyrektywy wygląda następująco:  
  
```  
#pragma omp flush [(variable-list)]  new-line  
```  
  
 Jeśli obiekty, które wymagają synchronizacji można wszystkie wyznacza zmiennych, a następnie tych zmiennych może zostać określony w opcjonalnym *zmiennej listy*. Jeśli wskaźnik znajduje się w *zmiennej listy*się wskaźnik myszy jest opróżniany, nie obiekt wskaźnika odnosi się do.  
  
 A **opróżnić** dyrektywy bez *zmiennej listy* synchronizuje wszystkich udostępnionych obiektów z wyjątkiem obiektów niedostępne z automatycznym okresem magazynu. (Jest to prawdopodobnie mają większe obciążenie niż **opróżnić** z *liście zmiennych*.) A **opróżnić** dyrektywy bez *zmiennej listy* technicznego dla dyrektywy następujące:  
  
-   `barrier`  
  
-   W wpisu i wyjście z **krytyczne**  
  
-   W wpisu i wyjście z`ordered`  
  
-   W wpisu i wyjście z **równoległych**  
  
-   At wyjść z **dla**  
  
-   At wyjść z **sekcje**  
  
-   At wyjść z **pojedynczego**  
  
-   W wpisu i wyjście z **równoległe w**  
  
-   W wpisu i wyjście z **sekcji równoległych**  
  
 Dyrektywa nie jest oznaczany, jeśli `nowait` klauzuli jest obecny. Należy zauważyć, że **opróżnić** dyrektywy nie jest oznaczany dla żadnej z następujących czynności:  
  
-   Wejścia do **dla**  
  
-   Wpis do lub wyjście z **wzorca**  
  
-   Wejścia do **sekcje**  
  
-   Wejścia do **pojedynczego**  
  
 Odwołania, który uzyskuje dostęp do wartości obiektu typu kwalifikowanego volatile zachowuje się jak w przypadku **opróżnić** dyrektywy określania tego obiektu w poprzednim punkcie sekwencji. Odwołanie, które modyfikuje wartości obiektu typu kwalifikowanego volatile zachowuje się jak w przypadku **opróżnić** dyrektywy określania tego obiektu w momencie kolejnych sekwencji.  
  
 Należy pamiętać, że ponieważ **opróżnić** dyrektywy nie ma instrukcji języka C w ramach jego składni, istnieją pewne ograniczenia na jej położenie w programie. Zobacz [dodatku C](../../parallel/openmp/c-openmp-c-and-cpp-grammar.md) dla formalnego gramatyki. W poniższym przykładzie przedstawiono te ograniczenia.  
  
```  
/* ERROR - The flush directive cannot be the immediate  
*          substatement of an if statement.  
*/  
if (x!=0)  
   #pragma omp flush (x)  
...  
  
/* OK - The flush directive is enclosed in a  
*      compound statement  
*/  
if (x!=0) {  
   #pragma omp flush (x)  
}  
```  
  
 Ograniczenia **opróżnić** dyrektywy są następujące:  
  
-   Określona w zmiennej **opróżnić** dyrektywy nie może mieć typu referencyjnego.