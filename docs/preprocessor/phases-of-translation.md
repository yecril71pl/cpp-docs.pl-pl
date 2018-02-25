---
title: "Fazy tłumaczenia | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- translation phases
- preprocessor, translation
- translation, compiler process
- preprocessor
- file translation [C++], compiler process
- files [C++], translation
ms.assetid: a7f7a8c9-e8ba-4321-9e50-ebfbbdcce9db
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 21cf6efeba83758bed8abe45aba36f025ace16f4
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="phases-of-translation"></a>Fazy tłumaczenia
Programy C i C++ składają się z jednego lub więcej plików źródłowych, z których każdy zawiera część tekstu programu. Plik źródłowy, wraz z dołączonymi plikami (plikami dołączonymi za pomocą dyrektywy preprocesora `#include`), ale bez sekcji kodu usuniętych przez dyrektywy kompilacji warunkowej takie jak `#if`, nosi nazwę „jednostki translacji”.  
  
 Pliki źródłowe mogą być tłumaczone w różnym czasie — w rzeczywistości bardzo często tłumaczone są tylko nieaktualne pliki. Przetłumaczone jednostki translacji mogą być przetwarzane do oddzielnych plików obiektu lub bibliotek kodu obiektu. Te oddzielne, przetłumaczone jednostki translacji są następnie łączone, aby sformułować program wykonywalny lub bibliotekę dynamicznych połączeń (DLL).  Aby uzyskać więcej informacji o plikach, które mogą być używane jako dane wejściowe konsolidatora, zobacz [plików wejściowych łącze](../build/reference/link-input-files.md).  
  
 Jednostki translacji mogą komunikować się za pomocą:  
  
-   Wywołań funkcji, które mają powiązania zewnętrzne.  
  
-   Wywołań funkcji składowych klasy, które mają powiązania zewnętrzne.  
  
-   Bezpośrednich modyfikacji obiektów, które mają powiązania zewnętrzne.  
  
-   Bezpośrednich modyfikacji plików.  
  
-   Komunikacji międzyprocesowej (tylko dla aplikacji opartych na Microsoft Windows).  
  
 Na poniższej liście opisano fazy, w których kompilator tłumaczy pliki:  
  
 *Mapowania znaków*  
 Znaki w pliku źródłowym są mapowane do wewnętrznej reprezentacji źródła. Sekwencje trzech znaków są konwertowane na wewnętrzną reprezentację pojedynczych znaków w tej fazie.  
  
 *Łączenia wierszy*  
 Wszystkie wiersze w ukośnik odwrotny (**\\**) i bezpośrednio po przy nowym wierszem znak są łączone z następnego wiersza w pliku źródłowym stanowiące logiczne wiersze z fizycznego wierszy. O ile nie jest on pusty, plik źródłowy musi kończyć się znakiem nowego wiersza, który nie jest poprzedzony znakiem ukośnika odwrotnego.  
  
 *Tokenizacji*  
 Plik źródłowy jest dzielony na tokeny wstępnego przetwarzania i znaki odstępu. Każdy komentarz w pliku źródłowym jest zamieniany na jeden znak spacji. Znaki nowego wiersza są zachowywane.  
  
 *Przetwarzanie wstępne*  
 Dyrektywy przetwarzania wstępnego są wykonywane, a makra rozwijane do pliku źródłowego. Instrukcja `#include` wywołuje translację począwszy od powyższych trzech kroków translacji na dowolnym dołączonym tekście.  
  
 *Mapowanie zestawu znaków*  
 Wszystkie elementy członkowskie zestawu znaków źródła i sekwencje unikowe są konwertowane na ich odpowiedniki w zestawie znaków wykonywania. Zestawy znaków źródła i wykonania są w kodowaniu ASCII w Microsoft C i C++.  
  
 *Łączenie ciągów*  
 Wszystkie sąsiadujące ciągi znaków i literały szerokiego ciągu są łączone. Na przykład, `"String " "concatenation"` staje się `"String concatenation"`.  
  
 *Tłumaczenie*  
 Wszystkie tokeny są analizowane składniowo i semantycznie; tokeny te są przekształcane na kod obiektu.  
  
 *Połączenie*  
 Wszystkie odwołania zewnętrzne są rozwiązywane, aby utworzyć program wykonywalny lub bibliotekę dołączaną dynamicznie.  
  
 Kompilator generuje ostrzeżenia lub błędy podczas faz tłumaczenia, w których napotka błędy składniowe.  
  
 Konsolidator usuwa wszystkie odwołania zewnętrzne i tworzy plik wykonywalny lub bibliotekę DLL przez połączenie jednej lub więcej jednostek translacji z bibliotekami standardowymi.  
  
## <a name="see-also"></a>Zobacz też  
 [Preprocesor](../preprocessor/preprocessor.md)