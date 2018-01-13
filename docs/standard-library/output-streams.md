---
title: "Strumienie wyjściowe | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: output streams
ms.assetid: b49410e3-5caa-4153-9d0d-c4266408dc83
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f8fee8ecffda86f306b44f0d5b873d5192d4d181
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="output-streams"></a>Strumienie wyjściowe
Obiekt strumień wyjściowy jest docelowy dla bajtów. Są trzy najważniejsze klasy strumienia wyjściowego `ostream`, `ofstream`, i `ostringstream`.  
  
 `ostream` Klasy za pomocą klasy pochodnej `basic_ostream`, obsługuje obiekty wstępnie zdefiniowanych strumienia:  
  
-   `cout`standardowe dane wyjściowe  
  
-   `cerr`Błąd standardowy z ograniczoną buforowania  
  
-   `clog`Podobnie jak `cerr` , ale pełne buforowanie  
  
 Obiekty rzadko są tworzone na podstawie `ostream`; wstępnie zdefiniowanych obiektów są zazwyczaj używane. W niektórych przypadkach można ponownie przypisać wstępnie zdefiniowanych obiektów po uruchomieniu programu. `ostream` Klasy, która może być skonfigurowana dla operacji buforowane lub Niebuforowane, najlepiej nadaje się do wyjścia sekwencyjnych tekstowej. Wszystkie funkcje klasy podstawowej, `ios`, znajduje się w `ostream`. W przypadku utworzenia obiektu klasy `ostream`, należy określić `streambuf` obiekt do konstruktora.  
  
 `ofstream` Klasa obsługuje dysku pliku wyjściowego. Dysk tylko do danych wyjściowych, należy utworzyć obiekt klasy `ofstream`. Można określić czy `ofstream` obiektów akceptować dane pliku binarnego lub trybie tekstowym podczas konstruowania `ofstream` obiektu lub podczas wywoływania metody `open` funkcji członkowskiej klasy obiektu. Wiele funkcji formatowania opcje i element członkowski dotyczą `ofstream` obiekty i wszystkie funkcje klasy podstawowe `ios` i `ostream` jest dołączony.  
  
 Jeśli w Konstruktorze określono nazwę pliku, jest automatycznie otworzyć tego pliku podczas konstruowania obiektu. W przeciwnym razie można użyć `open` funkcji członkowskiej po wywołaniu konstruktora domyślnego.  
  
 Funkcja środowiska wykonawczego, takich jak `sprintf_s`, `ostringstream` klasa obsługuje dane wyjściowe do ciągów w pamięci. Aby utworzyć ciąg w pamięci przy użyciu formatowania strumień we/wy, należy utworzyć obiekt klasy `ostringstream`.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Konstruowanie obiektów strumienia wyjściowego](../standard-library/constructing-output-stream-objects.md)  
  
 [Korzystanie z operatorów wstawiania i formatu kontrolującego](../standard-library/using-insertion-operators-and-controlling-format.md)  
  
 [Funkcje składowe strumienia pliku danych wyjściowych](../standard-library/output-file-stream-member-functions.md)  
  
 [Efekty buforowania](../standard-library/effects-of-buffering.md)  
  
 [Wyjściowe pliki binarne](../standard-library/binary-output-files.md)  
  
 [Przeciążanie operatora << dla własnych klas](../standard-library/overloading-the-output-operator-for-your-own-classes.md)  
  
 [Tworzenie manipulatorów bez argumentów](../standard-library/writing-your-own-manipulators-without-arguments.md)  
  
## <a name="see-also"></a>Zobacz też 
 [ofstream](../standard-library/basic-ofstream-class.md)   
 [ostringstream](../standard-library/basic-ostringstream-class.md)   
 [iostream, programowanie](../standard-library/iostream-programming.md)

