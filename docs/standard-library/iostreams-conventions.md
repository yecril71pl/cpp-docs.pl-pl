---
title: Konwencje iostream
ms.date: 11/04/2016
helpviewer_keywords:
- iostream header
- C++ Standard Library, iostreams
ms.assetid: 9fe5ded0-37a1-48d1-9671-c81ffc4760ad
ms.openlocfilehash: 52cdd06385994e49ff793e40318ca4cbbbcfcda0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50645565"
---
# <a name="iostreams-conventions"></a>Konwencje iostream

Nagłówki iostreams obsługi konwersji między tekst i zakodowany formularzy oraz dane wejściowe i wyjściowe do zewnętrznych plików:

|||
|-|-|
|[\<fstream>](../standard-library/fstream.md)|[\<iomanip >](../standard-library/iomanip.md)|
|[\<IOS >](../standard-library/ios.md)|[\<iosfwd>](../standard-library/iosfwd.md)|
|[\<iostream>](../standard-library/iostream.md)|[\<istream>](../standard-library/istream.md)|
|[\<ostream>](../standard-library/ostream.md)|[\<sstream — >](../standard-library/sstream.md)|
|[\<streambuf>](../standard-library/streambuf.md)|[\<strstream>](../standard-library/strstream.md)|

Najprostsze użycie iostreams wymaga jedynie, czy dołączyć nagłówek [ \<iostream >](../standard-library/iostream.md). Następnie można wyodrębnić wartości z [cin](../standard-library/iostream.md#cin) lub [wcin](../standard-library/iostream.md#wcin) odczytać standardowe dane wejściowe. Zasady dotyczące dostarczania więc są przedstawione opis klasy [basic_istream — klasa](../standard-library/basic-istream-class.md). Można także wstawić wartości [cout](../standard-library/iostream.md#cout) lub [wcout](../standard-library/iostream.md#wcout) do zapisu do wyjścia standardowego. Zasady dotyczące dostarczania więc są przedstawione opis klasy [basic_ostream — klasa](../standard-library/basic-ostream-class.md). Format wspólnych dla ekstraktory i insertors zarządzać przez klasę [basic_ios — klasa](../standard-library/basic-ios-class.md). Manipulowanie tego formatu informacji w podszywając wyodrębniania i wstawianie obiektów jest prowincji manipulatory kilka.

Można wykonać te same operacje iostreams na plikach, które otwierają według nazwy, za pomocą klasy zadeklarowanej w [ \<fstream — >](../standard-library/fstream.md). Aby wykonać konwersję między iostreams i obiektów klasy [basic_string — klasa](../standard-library/basic-string-class.md), użyj klasy zadeklarowanej w [ \<strumienia >](../standard-library/sstream.md). Aby zrobić z ciągami C, należy użyć klasy zadeklarowanej w [ \<strstream — >](../standard-library/strstream.md).

Pozostałe nagłówki świadczyć usług pomocy technicznej, zwykle orientacyjnego bezpośrednich do najbardziej zaawansowanych użytkowników klasy iostreams.

## <a name="see-also"></a>Zobacz także

[Standardowa biblioteka C++ — przegląd](../standard-library/cpp-standard-library-overview.md)<br/>
[iostream, programowanie](../standard-library/iostream-programming.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
