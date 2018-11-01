---
title: Input / Output Alternatives
ms.date: 11/04/2016
helpviewer_keywords:
- I/O [C++], alternatives
ms.assetid: 9f8401c7-d90d-4285-8918-63573df74a80
ms.openlocfilehash: bc595b64c991ada8e958e71e13f8cb9d134adb8a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50439692"
---
# <a name="inputoutput-alternatives"></a>Input/Output Alternatives

Visual C++ udostępnia kilka rozwiązań alternatywnych programowanie wejścia/wyjścia:

- C biblioteki wykonawczej bezpośrednie, Niebuforowane operacje We/Wy.

- We/Wy strumienia biblioteki wykonawczej C do ANSI.

- Konsoli i portu bezpośrednie we/wy.

- Biblioteki klas Microsoft Foundation.

- Microsoft standardowej bibliotece C++.

Iostream, które klasy są przydatne w przypadku buforowane, sformatowany tekst we/wy. Są one przydatne w przypadku operacji We/Wy Niebuforowane lub binarny również wtedy, jeśli potrzebujesz interfejs programowania C++ i nie chcesz używać biblioteki Microsoft Foundation Class (MFC). Klasy iostream — są zorientowane obiektowo operacji We/Wy alternatywa funkcje środowiska wykonawczego języka C.

W systemie operacyjnym Microsoft Windows, można użyć klasach iostream. Ciąg i plików strumieni pracy bez ograniczeń, ale obiekty strumienia tryb znakowy `cin`, `cout`, `cerr`, i `clog` są niespójne z Windows graficznego interfejsu użytkownika. Może również pochodzić klasy strumieni niestandardowych, wchodzących w interakcję bezpośrednio za pomocą środowiska Windows.

## <a name="see-also"></a>Zobacz także

[Czym jest strumień?](../standard-library/what-a-stream-is.md)<br/>
