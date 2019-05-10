---
title: Input / Output Alternatives
ms.date: 05/07/2019
helpviewer_keywords:
- I/O [C++], alternatives
ms.assetid: 9f8401c7-d90d-4285-8918-63573df74a80
ms.openlocfilehash: 5fb98714a96dedf725ea17332d7c1627e3390896
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2019
ms.locfileid: "65221391"
---
# <a name="inputoutput-alternatives"></a>Input/Output Alternatives

Microsoft C++ kompilator udostępnia kilka rozwiązań alternatywnych dla operacji We/Wy programowania:

- C biblioteki wykonawczej bezpośrednie, Niebuforowane operacje We/Wy.

- We/Wy strumienia biblioteki wykonawczej C do ANSI.

- Konsoli i portu bezpośrednie we/wy.

- Microsoft Foundation Class Library.

- Microsoft C++ Standard Library.

Iostream, które klasy są przydatne w przypadku buforowane, sformatowany tekst we/wy. Są one przydatne w przypadku operacji We/Wy Niebuforowane lub binarny również wtedy, jeśli potrzebujesz interfejs programowania C++ i nie chcesz używać biblioteki Microsoft Foundation Class (MFC). Klasy iostream — są zorientowane obiektowo operacji We/Wy alternatywa funkcje środowiska wykonawczego języka C.

W systemie operacyjnym Microsoft Windows, można użyć klasach iostream. Ciąg i plików strumieni pracy bez ograniczeń, ale obiekty strumienia tryb znakowy `cin`, `cout`, `cerr`, i `clog` są niespójne z Windows graficznego interfejsu użytkownika. Może również pochodzić klasy strumieni niestandardowych, wchodzących w interakcję bezpośrednio za pomocą środowiska Windows.

## <a name="see-also"></a>Zobacz także

[Czym jest strumień?](../standard-library/what-a-stream-is.md)<br/>
