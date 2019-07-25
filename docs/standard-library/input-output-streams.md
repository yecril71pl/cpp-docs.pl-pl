---
title: Strumienie danych wejściowych i wyjściowych
ms.date: 11/04/2016
helpviewer_keywords:
- I/O [C++], stream
- stream I/O
ms.assetid: 21a97566-91a7-42d6-b2f8-a4c16bc926f1
ms.openlocfilehash: 3d5344ede3a62375c4c8102d1fc39445518eb0c4
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68455270"
---
# <a name="inputoutput-streams"></a>Input/Output Streams

`basic_iostream`, który jest zdefiniowany w pliku \<nagłówka IStream >, jest szablonem klasy dla obiektów, które obsługują zarówno dane wejściowe, jak i wyjściowe strumienie we/wy.

Istnieją dwa definicje typów, które definiują specjalizacje charakterystyczne dla `basic_iostream` znaków i mogą ułatwić odczytywanie kodu: `iostream` (nie należy mylić z plikiem \<nagłówka iostream >) to strumień we/wy oparty na `basic_iostream<char>`; to strumień we/wy oparty na `basic_iostream<wchar_t>`. `wiostream`

Aby uzyskać więcej informacji, zobacz [Basic_iostream Class](../standard-library/basic-iostream-class.md), [iostream](../standard-library/basic-iostream-class.md)i [wiostream](../standard-library/basic-iostream-class.md).

Pochodny od `basic_iostream` to szablon `basic_fstream`klasy, który jest używany do przesyłania strumieniowego danych do i z plików.

Istnieją również definicje typów, które zapewniają specjalizację specyficzną dla `basic_fstream`znaków. Są to `fstream`, czyli strumień we/wy pliku oparty `wfstream`na znakach, który jest strumieniem we/wy pliku opartym na **wchar_t**. Aby uzyskać więcej informacji, zobacz [Basic_fstream Class](../standard-library/basic-fstream-class.md), [fstream —](../standard-library/basic-fstream-class.md)i [wfstream](../standard-library/basic-fstream-class.md). Użycie tych elementów typedef wymaga włączenia pliku \<nagłówka fstream — >.

> [!NOTE]
> `basic_fstream` Gdy obiekt jest używany do wykonywania operacji we/wy na plikach, chociaż bazowy bufor zawiera oddzielnie wskazane położenia do odczytu i zapisu, bieżące wejściowe i bieżące pozycje wyjściowe są powiązane ze sobą, a tym samym odczytywanie niektórych danych przenosi Pozycja wyjściowa.

Szablon `basic_stringstream` klasy i jego wspólna specjalizacja `stringstream`, są często używane do pracy z obiektami strumienia we/wy w celu wstawiania i wyodrębniania danych znakowych. Aby uzyskać więcej informacji, zobacz [Klasa basic_stringstream](../standard-library/basic-stringstream-class.md).

## <a name="see-also"></a>Zobacz także

[stringstream](../standard-library/basic-stringstream-class.md)\
[Klasa basic_stringstream](../standard-library/basic-stringstream-class.md)\
[\<sstream>](../standard-library/sstream.md)\
[Programowanie iostream](../standard-library/iostream-programming.md)\
[Standardowa biblioteka C++](../standard-library/cpp-standard-library-reference.md)
