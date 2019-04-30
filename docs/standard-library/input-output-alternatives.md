---
title: Input / Output Alternatives
ms.date: 11/04/2016
helpviewer_keywords:
- I/O [C++], alternatives
ms.assetid: 9f8401c7-d90d-4285-8918-63573df74a80
ms.openlocfilehash: bc595b64c991ada8e958e71e13f8cb9d134adb8a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62404965"
---
# <a name="inputoutput-alternatives"></a>Input/Output Alternatives

Visual C++ udostępnia kilka rozwiązań alternatywnych programowanie wejścia/wyjścia:

- C biblioteki wykonawczej bezpośrednie, Niebuforowane operacje We/Wy.

- We/Wy strumienia biblioteki wykonawczej C do ANSI.

- Konsoli i portu bezpośrednie we/wy.

- Microsoft Foundation Class Library.

- Microsoft C++ Standard Library.

Iostream, które klasy są przydatne w przypadku buforowane, sformatowany tekst we/wy. Są one przydatne w przypadku operacji We/Wy Niebuforowane lub binarny również wtedy, jeśli potrzebujesz interfejs programowania C++ i nie chcesz używać biblioteki Microsoft Foundation Class (MFC). Klasy iostream — są zorientowane obiektowo operacji We/Wy alternatywa funkcje środowiska wykonawczego języka C.

W systemie operacyjnym Microsoft Windows, można użyć klasach iostream. Ciąg i plików strumieni pracy bez ograniczeń, ale obiekty strumienia tryb znakowy `cin`, `cout`, `cerr`, i `clog` są niespójne z Windows graficznego interfejsu użytkownika. Może również pochodzić klasy strumieni niestandardowych, wchodzących w interakcję bezpośrednio za pomocą środowiska Windows.

## <a name="see-also"></a>Zobacz także

[Czym jest strumień?](../standard-library/what-a-stream-is.md)<br/>
