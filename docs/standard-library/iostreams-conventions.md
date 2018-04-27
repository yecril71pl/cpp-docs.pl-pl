---
title: Konwencje iostream | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- iostream header
- C++ Standard Library, iostreams
ms.assetid: 9fe5ded0-37a1-48d1-9671-c81ffc4760ad
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8d5d6408f51bc3a0bf0fc0ca997635c5b371dcf6
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="iostreams-conventions"></a>Konwencje iostream

Nagłówki iostream obsługuje konwersje między tekst i zakodowanego formularzy i dane wejściowe i wyjściowe do zewnętrznych plików:

|||
|-|-|
|[\<fstream>](../standard-library/fstream.md)|[\<iomanip — >](../standard-library/iomanip.md)|
|[\<IOS >](../standard-library/ios.md)|[\<iosfwd>](../standard-library/iosfwd.md)|
|[\<iostream>](../standard-library/iostream.md)|[\<istream>](../standard-library/istream.md)|
|[\<ostream>](../standard-library/ostream.md)|[\<sstream — >](../standard-library/sstream.md)|
|[\<streambuf>](../standard-library/streambuf.md)|[\<strstream>](../standard-library/strstream.md)|

Najprostsza stosowania iostream wymaga jedynie, że Dołącz nagłówek [ \<iostream >](../standard-library/iostream.md). Następnie można wyodrębnić wartości z [cin](../standard-library/iostream.md#cin) lub [wcin](../standard-library/iostream.md#wcin) odczytać standardowe dane wejściowe. Zasady dotyczące dostarczania tak są opisane w temacie opis klasy [basic_istream — klasa](../standard-library/basic-istream-class.md). Można także wstawić wartości [cout](../standard-library/iostream.md#cout) lub [wcout](../standard-library/iostream.md#wcout) zapisu wyjścia standardowego. Zasady dotyczące dostarczania tak są opisane w temacie opis klasy [basic_ostream — klasa](../standard-library/basic-ostream-class.md). Format wspólne dla ekstraktory i insertors zarządzać przez klasę [basic_ios — klasa](../standard-library/basic-ios-class.md). Manipulowanie informację format podszywając wyodrębnianie i wstawianie obiektów jest właściwością kilka manipulatory.

Można wykonać operacji iostream na plikach, które możesz otworzyć według nazwy, za pomocą klasy zadeklarowany w [ \<fstream — >](../standard-library/fstream.md). Aby dokonać konwersji między iostream i obiektów klasy [basic_string — klasa](../standard-library/basic-string-class.md), użyj klasy zadeklarowany w [ \<sstream — >](../standard-library/sstream.md). Taki sam jak ciągi C, użyć klasy zadeklarowany w [ \<strstream — >](../standard-library/strstream.md).

Pozostałe nagłówki świadczenia usług pomocy technicznej, zwykle płynących bezpośrednio do najbardziej zaawansowanych użytkowników klasach iostream.

## <a name="see-also"></a>Zobacz także

[Standardowa biblioteka C++ — przegląd](../standard-library/cpp-standard-library-overview.md)<br/>
[iostream, programowanie](../standard-library/iostream-programming.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
