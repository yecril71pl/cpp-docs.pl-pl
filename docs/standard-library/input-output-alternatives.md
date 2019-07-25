---
title: Dane wejściowe danych wejściowych i wyjściowych
ms.date: 05/07/2019
helpviewer_keywords:
- I/O [C++], alternatives
ms.assetid: 9f8401c7-d90d-4285-8918-63573df74a80
ms.openlocfilehash: b46ff242fc263be5069eb691dd0ea9e8fb00b0f9
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68455290"
---
# <a name="inputoutput-alternatives"></a>Input/Output Alternatives

Kompilator firmy C++ Microsoft oferuje kilka alternatywnych rozwiązań programistycznych we/wy:

- Biblioteka wykonawcza języka C bezpośrednio, niebuforowane we/wy.

- Strumień operacji we/wy biblioteki wykonawczej ANSI C.

- Bezpośrednie we/wy konsoli i portu.

- Biblioteka MFC.

- Standardowa C++ Biblioteka firmy Microsoft.

Klasy iostream są przydatne w przypadku buforowanych, sformatowanych we/wy tekstu. Są one również przydatne dla niebuforowanego lub binarnego wejścia/wyjścia, jeśli potrzebujesz C++ interfejsu programowania i nie będą używać biblioteki Microsoft Foundation Class (MFC). Klasy iostream są alternatywnym obiektem we/wy dla funkcji w czasie wykonywania języka C.

Klas iostream można użyć z systemem operacyjnym Microsoft Windows. Strumienie ciągów i plików działają bez ograniczeń, `cin`ale obiekty strumienia trybu znakowego `cerr`, `cout`, i `clog` są niespójne z graficznym interfejsem użytkownika systemu Windows. Można również utworzyć niestandardowe klasy strumienia, które współpracują bezpośrednio ze środowiskiem systemu Windows.

## <a name="see-also"></a>Zobacz także

[Czym jest strumień?](../standard-library/what-a-stream-is.md)
