---
title: Konwencje iostream
ms.date: 11/04/2016
helpviewer_keywords:
- iostream header
- C++ Standard Library, iostreams
ms.assetid: 9fe5ded0-37a1-48d1-9671-c81ffc4760ad
ms.openlocfilehash: 7bfc497ec7c55a611d29cd62d076c0ac2e9b6e9f
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88845461"
---
# <a name="iostreams-conventions"></a>Konwencje iostream

Nagłówki iostreams obsługują konwersje pomiędzy tekstem i zakodowanymi formularzami, a wejściem i wyjściem do plików zewnętrznych:

[\<fstream>](../standard-library/fstream.md)\
[\<iomanip>](../standard-library/iomanip.md)\
[\<ios>](../standard-library/ios.md)\
[\<iosfwd>](../standard-library/iosfwd.md)\
[\<iostream>](../standard-library/iostream.md)\
[\<istream>](../standard-library/istream.md)\
[\<ostream>](../standard-library/ostream.md)\
[\<sstream>](../standard-library/sstream.md)\
[\<streambuf>](../standard-library/streambuf.md)\
[\<strstream>](../standard-library/strstream.md)

Najprostsza użycie iostreams wymaga tylko dołączenia nagłówka [\<iostream>](../standard-library/iostream.md) . Następnie można wyodrębnić wartości z [CIN](../standard-library/iostream.md#cin) lub [wcin](../standard-library/iostream.md#wcin) , aby odczytać standardowe dane wejściowe. Reguły, które należy wykonać, są opisane w opisie klasy [Basic_istream klasie](../standard-library/basic-istream-class.md). Możesz również wstawić wartości do [cout](../standard-library/iostream.md#cout) lub [wcout](../standard-library/iostream.md#wcout) , aby napisać standardowe dane wyjściowe. Reguły, które należy wykonać, są opisane w opisie klasy [Basic_ostream klasie](../standard-library/basic-ostream-class.md). Kontrolka formatu wspólna dla obydwu ekstraktorów i wstawek jest zarządzana przez klasę klasy [basic_ios](../standard-library/basic-ios-class.md). Manipulowanie tym formatem informacjami w Guise wyodrębniania i wstawiania obiektów jest prowincją kilku manipulowania.

Te same operacje iostreams na plikach, które są otwierane przez nazwę, można wykonać przy użyciu klas zadeklarowanych w elemencie [\<fstream>](../standard-library/fstream.md) . Aby przeprowadzić konwersję między iostreams i obiektami [klasy basic_string](../standard-library/basic-string-class.md), użyj klas zadeklarowanych w elemencie [\<sstream>](../standard-library/sstream.md) . Aby zrobić to samo w przypadku ciągów języka C, użyj klas zadeklarowanych w elemencie [\<strstream>](../standard-library/strstream.md) .

Pozostałe nagłówki zapewniają usługi pomocy technicznej, zwykle są bezpośrednio przydatne tylko dla najbardziej zaawansowanych użytkowników klas iostreams.

## <a name="see-also"></a>Zobacz też

[Omówienie standardowej biblioteki języka C++](../standard-library/cpp-standard-library-overview.md)\
[Programowanie iostream](../standard-library/iostream-programming.md)\
[Bezpieczeństwo wątku w standardowej bibliotece języka C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
