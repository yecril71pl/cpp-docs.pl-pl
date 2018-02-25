---
title: Strumienie | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- reading data [C++], from input streams
- data [C++], reading from input stream
- input streams
- input stream objects
ms.assetid: f14d8954-8f8c-4c3c-8b99-14ddb3683f94
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c7844ebbdc3614783a92283f573422834b1c2fce
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="input-streams"></a>Strumienie wejściowe
Obiekt strumień wejściowy jest źródłem bajtów. Są trzy najważniejsze klasy strumień wejściowy [istream](../standard-library/basic-istream-class.md), [ifstream](../standard-library/basic-ifstream-class.md), i [istringstream](../standard-library/basic-istringstream-class.md).  
  
 `istream` Klasy najlepiej nadaje się do danych wejściowych sekwencyjnych tekstowej. Można skonfigurować obiektów klasy `istream` buforowane lub Niebuforowane operacji. Wszystkie funkcje klasy podstawowej, `ios`, znajduje się w `istream`. Rzadko utworzy obiekty z klasy `istream`. Zamiast tego zazwyczaj użyje wstępnie zdefiniowane `cin` obiektu, który jest rzeczywiście obiekt klasy [ostream](../standard-library/basic-ostream-class.md). W niektórych przypadkach można przypisać `cin` do innych obiektów strumienia po uruchomieniu programu.  
  
 `ifstream` Klasa obsługuje wejście dysku. Jeśli potrzebujesz tylko wejściowym na dysku, utworzenia obiektu klasy `ifstream`. Można określić danych binarnych lub tekstowej. Jeśli w Konstruktorze określono nazwę pliku, plik jest otwarty automatycznie, podczas konstruowania obiektu. W przeciwnym razie można użyć `open` funkcja po wywołaniu konstruktora domyślnego. Wiele funkcji formatowania opcje i element członkowski dotyczą `ifstream` obiektów. Wszystkie funkcje klasy podstawowe `ios` i `istream` znajduje się w `ifstream`.  
  
 Funkcja biblioteki, takich jak `sscanf_s`, `istringstream` klasa obsługuje dane wejściowe z ciągów w pamięci. Aby wyodrębnić dane z tablicy znaków, które ma terminatorem null, alokacji i inicjuje ciąg, a następnie utworzyć obiekt klasy `istringstream`.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Konstruowanie obiektów strumienia danych wejściowych](../standard-library/constructing-input-stream-objects.md)  
  
 [Korzystanie z operatorów wyodrębniania](../standard-library/using-extraction-operators.md)  
  
 [Testowanie pod kątem wyodrębniania błędów](../standard-library/testing-for-extraction-errors.md)  
  
 [Manipulatory strumieni wejścia](../standard-library/input-stream-manipulators.md)  
  
 [Funkcje składowe strumienia wejściowego](../standard-library/input-stream-member-functions.md)  
  
 [Przeciążanie operatora >> dla własnych klas](../standard-library/overloading-the-input-operator-for-your-own-classes.md)  
  
## <a name="see-also"></a>Zobacz też  
 [iostream, programowanie](../standard-library/iostream-programming.md)
