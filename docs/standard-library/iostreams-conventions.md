---
title: Konwencje iostream
ms.date: 11/04/2016
helpviewer_keywords:
- iostream header
- C++ Standard Library, iostreams
ms.assetid: 9fe5ded0-37a1-48d1-9671-c81ffc4760ad
ms.openlocfilehash: 222a65f60b231ba4b3768131c15d6e0d736f211e
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68449014"
---
# <a name="iostreams-conventions"></a>Konwencje iostream

Nagłówki iostreams obsługują konwersje pomiędzy tekstem i zakodowanymi formularzami, a wejściem i wyjściem do plików zewnętrznych:

|||
|-|-|
|[\<fstream>](../standard-library/fstream.md)|[\<iomanip >](../standard-library/iomanip.md)|
|[\<> systemu iOS](../standard-library/ios.md)|[\<iosfwd>](../standard-library/iosfwd.md)|
|[\<iostream>](../standard-library/iostream.md)|[\<istream>](../standard-library/istream.md)|
|[\<ostream>](../standard-library/ostream.md)|[\<strumienia >](../standard-library/sstream.md)|
|[\<streambuf>](../standard-library/streambuf.md)|[\<strstream>](../standard-library/strstream.md)|

Najprostsza użycie iostreams wymaga tylko dołączenia nagłówka [ \<iostream >](../standard-library/iostream.md). Następnie można wyodrębnić wartości z [CIN](../standard-library/iostream.md#cin) lub [wcin](../standard-library/iostream.md#wcin) , aby odczytać standardowe dane wejściowe. Reguły, które należy wykonać, są opisane w opisie klasy klasy [basic_istream](../standard-library/basic-istream-class.md). Możesz również wstawić wartości do [cout](../standard-library/iostream.md#cout) lub [wcout](../standard-library/iostream.md#wcout) , aby napisać standardowe dane wyjściowe. Reguły, które należy wykonać, są opisane w opisie klasy klasy [basic_ostream](../standard-library/basic-ostream-class.md). Kontrolka formatu wspólna dla obu ekstraktorów i wstawek jest zarządzana przez klasę klasy [basic_ios](../standard-library/basic-ios-class.md). Manipulowanie tym formatem informacjami w Guise wyodrębniania i wstawiania obiektów jest prowincją kilku manipulowania.

Te same operacje iostreams na plikach, które są otwierane przez nazwę, można wykonać przy użyciu klas zadeklarowanych w [ \<fstream — >](../standard-library/fstream.md). Aby przeprowadzić konwersję między iostreams i obiektami [klasy klasy basic_string](../standard-library/basic-string-class.md), użyj klas zadeklarowanych w [ \<strumienia >](../standard-library/sstream.md). Aby zrobić to samo w przypadku ciągów języka C, użyj klas zadeklarowanych w [ \<strstream >](../standard-library/strstream.md).

Pozostałe nagłówki zapewniają usługi pomocy technicznej, zwykle są bezpośrednio przydatne tylko dla najbardziej zaawansowanych użytkowników klas iostreams.

## <a name="see-also"></a>Zobacz także

[C++Omówienie biblioteki standardowej](../standard-library/cpp-standard-library-overview.md)\
[Programowanie iostream](../standard-library/iostream-programming.md)\
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
